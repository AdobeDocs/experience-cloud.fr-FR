---
title: Guide d’intégration de l’extension Experience Rollout pour iOS
description: Découvrez comment intégrer l’extension Experience Rollout à Adobe Experience Platform Mobile SDK sur iOS.
source-git-commit: a9f6746c2b470377d2fd58de18e984d1ec404a77
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 8%

---

# Extension Experience Rollout pour iOS {#ios-extension-integration-guide}

Ce guide décrit comment intégrer l’extension Experience Rollout à Adobe Experience Platform Mobile SDK sur iOS.

## Conditions préalables {#prerequisites}

Avant de mettre en œuvre l’extension Déploiement d’expérience , vérifiez que vous disposez des éléments suivants :

* Propriété mobile configurée dans la collecte de données Adobe Experience Platform [&#128279;](https://experience.adobe.com/#/data-collection)
* Extension Experience Rollout installée et configurée dans votre propriété mobile
* Un identifiant d’organisation Adobe Experience Cloud
* Cible de déploiement minimale : iOS 12.0
* Xcode 14.1 ou version ultérieure

## Dépendances d’extension {#extension-dependencies}

L’extension Experience Rollout requiert les extensions Adobe Experience Platform suivantes :

| Extension | Description | Obligatoire |
|---|---|---|
| Mobile Core | Fournit des fonctionnalités de base, notamment la configuration et le traitement des événements | Oui |
| Cycle de vie | Collecte les données de session et de cycle de vie des applications pour Mobile SDK | Oui |
| Edge Network | Permet la communication avec Adobe Experience Platform Edge Network. | Oui |
| Identité Edge | Gère l’identité de l’utilisateur pour Edge Network | Oui |

Assurez-vous que ces extensions sont installées dans votre propriété mobile de collecte de données et incluses dans vos dépendances d’application.

## Configurer l’extension de déploiement d’expérience dans la collecte de données {#configure}

### Installation l’extension {#install-extension}

1. Connectez-vous à [Collecte de données &#x200B;](https://experience.adobe.com/#/data-collection).
1. Sélectionnez l’onglet **Balises** et choisissez votre propriété mobile.
1. Accédez à **Extensions** > **Catalogue**.
1. Recherchez **Extension du déploiement d’expérience** et sélectionnez **Installer**.
1. Configurez les paramètres d’extension :

   | Paramètre | Description |
   |---|---|
   | Sandbox | Le sandbox Adobe Experience Platform contenant votre configuration de déploiement d’expérience |
   | ID de l’application | Identifiant unique de votre application dans le déploiement d’expérience |
   | Identifiant du jeu de données | Identifiant du jeu de données Adobe Experience Platform pour les données d’événement Analytics |

1. Sélectionnez **Enregistrer**.
1. Suivez le [processus de publication](https://experienceleague.adobe.com/fr/docs/experience-platform/tags/publish/overview) pour mettre à jour votre configuration.

### Obtention de l’identifiant du fichier d’environnement {#environment-file-id}

1. Dans votre propriété mobile, accédez à **Environnements**.
1. Sélectionnez l’icône en forme de boîte sous la colonne **Installer** pour votre environnement.
1. Dans la boîte de dialogue **Instructions d’installation mobile**, copiez le **ID du fichier d’environnement**.

## Ajout de l’extension Experience Rollout à votre application {#add-to-app}

### Ajouter des dépendances {#add-dependencies}

Ajoutez les dépendances Mobile SDK à votre projet. L’extension Experience Rollout nécessite Mobile Core et les extensions associées à Edge répertoriées ci-dessous.

#### Utilisation Du Gestionnaire De Packages Swift (Recommandé) {#swift-package-manager}

1. Dans Xcode, accédez à **Fichier** > **Ajouter des dépendances de package**.
1. Saisissez l’URL du référentiel Adobe Experience Platform Mobile SDK :

   ```
   https://github.com/adobe/aepsdk-core-ios
   ```

1. Ajoutez les packages suivants :

   | Package | Référentiel |
   |---|---|
   | AEPCore, AEPLifecycle | `https://github.com/adobe/aepsdk-core-ios` |
   | AEPEdge | `https://github.com/adobe/aepsdk-edge-ios` |
   | AEPdgeIdentity | `https://github.com/adobe/aepsdk-edgeidentity-ios` |
   | AEPRollout | `https://github.com/adobe/aepsdk-rollout-ios` |

#### Utilisation de cocoaPods {#cocoapods}

Ajoutez les capsules suivantes à votre `Podfile` :

```ruby
pod 'AEPCore'
pod 'AEPLifecycle'
pod 'AEPEdge'
pod 'AEPEdgeIdentity'
pod 'AEPRollout'
```

Exécutez ensuite :

```bash
pod install
```

>[!IMPORTANT]
>
>Pour les applications de production, Adobe recommande d’épingler des numéros de version explicites au lieu d’utiliser des plages `~>` ou ouvertes. Pour plus d’informations[&#128279;](https://guides.cocoapods.org/using/the-podfile.html) consultez le guide de contrôle de version CocoaPods .

### Initialiser le SDK {#initialize-sdk}

Initialisez Mobile SDK dans votre `AppDelegate` (ou `SceneDelegate`) avant d’appeler les API d’extension de déploiement d’expérience. Utilisez l’identifiant du fichier d’environnement de votre propriété mobile afin que l’application récupère les paramètres de déploiement que vous avez publiés dans la collecte de données.

**Swift**

```swift
import AEPCore
import AEPLifecycle
import AEPEdge
import AEPEdgeIdentity
import AEPRollout

@main
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(
        _ application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?
    ) -> Bool {

        MobileCore.setLogLevel(.error)

        MobileCore.registerExtensions(
            [Lifecycle.self, Edge.self, Identity.self, Rollout.self]
        ) {
            // Initialize with your Environment File ID from Data Collection
            MobileCore.configureWith(appId: "YOUR_ENVIRONMENT_FILE_ID")
        }

        return true
    }
}
```

**Objectif-C**

```objc
@import AEPCore;
@import AEPLifecycle;
@import AEPEdge;
@import AEPEdgeIdentity;
@import AEPRollout;

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application
    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [AEPMobileCore setLogLevel:AEPLogLevelError];

    NSArray *extensions = @[
        AEPMobileLifecycle.class,
        AEPMobileEdge.class,
        AEPMobileEdgeIdentity.class,
        AEPMobileRollout.class
    ];

    [AEPMobileCore registerExtensions:extensions completion:^{
        // Initialize with your Environment File ID from Data Collection
        [AEPMobileCore configureWithAppId:@"YOUR_ENVIRONMENT_FILE_ID"];
    }];

    return YES;
}

@end
```

>[!IMPORTANT]
>
>Pour les applications de production, utilisez `LogLevel.error` uniquement. N’utilisez ni `.debug` ni `.verbose` dans les builds de version.

## Contexte d’évaluation {#evaluation-context}

`FeatureEvaluationContext` inclut les attributs de ciblage (utilisés pour la correspondance des règles de déploiement) et l’identité facultative (utilisée pour les analyses).

| Méthode | Obligatoire | Description |
|---|---|---|
| `withIdentity(namespace:id:)` | Non | Premier argument : espace de noms d’identité (voir [Espaces de noms d’identité &#x200B;](https://experienceleague.adobe.com/fr/docs/experience-platform/identity/features/namespaces)). Deuxième argument : valeur de l&#39;identité. Incluez-le lorsque vous souhaitez que cet espace de noms et cet identifiant soient représentés dans Analytics pour cette évaluation. S’il n’est pas fourni, Analytics utilise ECID par défaut. Cela n’est pas utilisé pour prendre des décisions d’activation de fonctionnalités. |
| `withAttributes(_:)` | Non | `[String: [String]]`. Clé est le nom de l’attribut de contexte utilisé par vos règles de déploiement (par exemple, `locale`, `platform`, `appVersion`, `deviceType`). Valeur est la liste des valeurs d’attribut candidates pour cette clé pour l’utilisateur/la session en cours (par exemple `["en_US"]` ou `["phone"]`). |

**Swift**

```swift
import AEPRollout

let attrs: [String: [String]] = [
    "locale": ["en_US"],
    "platform": ["IOS"],
    "appVersion": ["3.0.0"]
]

let ctx = FeatureEvaluationContext.builder()
    .withIdentity(namespace: "Email", id: "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Objectif-C**

```objc
@import AEPRollout;

NSDictionary<NSString *, NSArray<NSString *> *> *attrs = @{
    @"locale": @[@"en_US"],
    @"platform": @[@"IOS"],
    @"appVersion": @[@"3.0.0"]
};

AEPFeatureEvaluationContext *ctx = [[[AEPFeatureEvaluationContextBuilder builder]
    withIdentityNamespace:@"Email" id:@"customer@example.com"]
    withAttributes:attrs]
    .build;
```

### Exemples d’attributs de ciblage {#sample-attributes}

| Attribut | Description | Exemples de valeurs |
|---|---|---|
| `locale` | Paramètres régionaux/langue de l’utilisateur | `["en_US"]`, `["fr_FR"]` |
| `platform` | Identifiant de plateforme | `["IOS"]` |
| `appVersion` | Version de l’application | `["3.0.0"]` |
| `deviceType` | Type d’appareil | `["phone"]`, `["tablet"]` |

## Référence d’API {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` indique si la fonction Déploiement d’expérience est activée ou désactivée pour le contexte donné. Transmettez des `featureKey`, un `FeatureEvaluationContext` (attributs de ciblage facultatifs et identité facultative pour Analytics) et un gestionnaire d’achèvement. Voir [&#x200B; Contexte d’évaluation &#x200B;](#evaluation-context).

**Signature**

*Swift*

```swift
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    completion: @escaping (Bool) -> Void
)
```

*Objectif-C*

```objc
[AEPMobileRollout isFeatureEnabled:(NSString *)featureKey
               evaluationContext:(AEPFeatureEvaluationContext *)evaluationContext
                      completion:(void (^)(BOOL))completion];
```

**Paramètres**

| Paramètre | Type | Description |
|---|---|---|
| `featureKey` | Chaîne | Clé de fonctionnalité à évaluer dans le déploiement d’expérience |
| `evaluationContext` | FeatureEvaluationContext | Ajoutez des attributs de ciblage et une identité facultative pour les analyses, au besoin ; utilisez `FeatureEvaluationContext.builder().build()` pour un contexte vide. Voir [&#x200B; Contexte d’évaluation &#x200B;](#evaluation-context). |
| `completion` | `(Bool) -> Void` | Appelé avec `true` si la fonctionnalité est activée, `false` dans le cas contraire. |

**Exemples**

*Swift*

```swift
import AEPRollout

Rollout.isFeatureEnabled(
    featureKey: "new-checkout-experience",
    evaluationContext: ctx
) { isEnabled in
    if isEnabled {
        showNewCheckout()
    } else {
        showDefaultCheckout()
    }
}
```

*Objectif-C*

```objc
@import AEPRollout;

[AEPMobileRollout isFeatureEnabled:@"new-checkout-experience"
               evaluationContext:ctx
                      completion:^(BOOL isEnabled) {
    if (isEnabled) {
        [self showNewCheckout];
    } else {
        [self showDefaultCheckout];
    }
}];
```

### getFeature {#get-feature}

`getFeature` renvoie la payload de fonction évaluée pour le contexte fourni. Utilisez cette API lorsque vous avez besoin de plus que activés/désactivés et que vous souhaitez obtenir des métadonnées ou des valeurs de fonctionnalités.

**Signature**

*Swift*

```swift
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    completion: @escaping (FeatureEvaluationResult?) -> Void
)
```

*Objectif-C*

```objc
[AEPMobileRollout getFeature:(NSString *)featureKey
         evaluationContext:(AEPFeatureEvaluationContext *)evaluationContext
                completion:(void (^)(AEPFeatureEvaluationResult * _Nullable))completion];
```

**Paramètres**

| Paramètre | Type | Description |
|---|---|---|
| `featureKey` | Chaîne | Clé de fonctionnalité à évaluer dans le déploiement d’expérience |
| `evaluationContext` | FeatureEvaluationContext | Ajoutez des attributs de ciblage et une identité facultative pour les analyses, au besoin ; utilisez `FeatureEvaluationContext.builder().build()` pour un contexte vide. Voir [&#x200B; Contexte d’évaluation &#x200B;](#evaluation-context). |
| `completion` | `(FeatureEvaluationResult?) -> Void` | Appelé avec la payload de la fonctionnalité évaluée ; peut être `nil` lorsque la fonctionnalité est introuvable. |

**Réponse**

*FeatureEvaluationResult*

| Champ | Type | Description |
|---|---|---|
| `id` | Int | Identifiant numérique de la caractéristique |
| `key` | Chaîne | Clé de fonctionnalité |
| `releaseKey` | Chaîne ? | Clé de mise à jour de cette fonctionnalité lorsqu’elle est disponible |
| `meta` | Chaîne ? | Métadonnées sous forme de chaîne JSON, le cas échéant |
| `analyticsParam` | AnalyticsParam ? | Détails Analytics pour la fonctionnalité évaluée |

*AnalyticsParam*

| Champ | Type | Description |
|---|---|---|
| `releaseId` | Int | Identifiant numérique de version |
| `featureId` | Int | Identifiant numérique de la caractéristique |
| `variantId` | Chaîne ? | Identifiant de la variante |

**Exemples**

*Swift*

```swift
import AEPRollout

Rollout.getFeature(
    featureKey: "new-checkout-experience",
    evaluationContext: ctx
) { feature in
    if let meta = feature?.meta, !meta.isEmpty {
        applyMetaDrivenExperience(meta)
    } else {
        showFallbackExperience()
    }
}
```

*Objectif-C*

```objc
@import AEPRollout;

[AEPMobileRollout getFeature:@"new-checkout-experience"
         evaluationContext:ctx
                completion:^(AEPFeatureEvaluationResult * _Nullable feature) {
    NSString *meta = feature.meta;
    if (meta != nil && meta.length > 0) {
        [self applyMetaDrivenExperience:meta];
    } else {
        [self showFallbackExperience];
    }
}];
```

### refreshCache {#refresh-cache}

Par défaut, l’extension Experience Rollout synchronise régulièrement les dernières règles et fonctionnalités de déploiement du serveur selon un planning que vous pouvez configurer. Si vous avez besoin d’une mise à jour avant la prochaine synchronisation planifiée, appelez `refreshCache` pour forcer une actualisation. Les cas types incluent après la connexion ou lorsque l’état de l’application change d’une manière qui doit affecter le ciblage.

**Syntaxe**

*Swift*

```swift
Rollout.refreshCache()
```

*Objectif-C*

```objc
[AEPMobileRollout refreshCache];
```

### extensionVersion {#extension-version}

Renvoie la chaîne de version de l’extension Experience Rollout.

**Syntaxe**

```swift
Rollout.extensionVersion(): String
```

**Exemple**

*Swift*

```swift
let version = Rollout.extensionVersion()
```

*Objectif-C*

```objc
NSString *version = [AEPMobileRollout extensionVersion];
```

## Résumé des API {#api-summary}

| API | Retours |
|---|---|
| `isFeatureEnabled(featureKey:evaluationContext:completion:)`. `FeatureEvaluationContext` transporte les attributs de ciblage pour les règles et l’identité facultative pour les analyses. Voir [isFeatureEnabled](#is-feature-enabled). | Booléen via le gestionnaire d’achèvement |
| `getFeature(featureKey:evaluationContext:completion:)`. Renvoie la payload de fonction évaluée pour le contexte donné. Voir [getFeature](#get-feature). | FeatureEvaluationResult ? via le gestionnaire d’achèvement |
| `refreshCache()` | Annuler |
| `extensionVersion()` | Chaîne |

## Voir également {#see-also}

* [Applications mobiles](../../integrate/mobile-applications.md)
* [Étapes d’intégration](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)
* [Guide d’intégration de l’extension Android](../android/android-extension-integration-guide.md)
