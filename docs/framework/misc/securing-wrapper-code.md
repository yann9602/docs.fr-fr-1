---
title: "S&#233;curisation du code wrapper | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sécurité du code, code wrapper"
  - "codage sécurisé, code wrapper"
  - "sécurité (.NET Framework), code wrapper"
  - "code wrapper, sécuriser"
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# S&#233;curisation du code wrapper
Le code wrapper, en particulier quand le wrapper est d'un niveau de confiance supérieur au code qui l'utilise, peut faire apparaître un ensemble unique de failles en matière de sécurité. Toutes les opérations effectuées au nom d'un appelant, où les autorisations limitées de l'appelant ne sont pas incluses dans la vérification de sécurité appropriée, constituent une faille potentielle exploitable.  
  
 N'autorisez jamais une opération par l'intermédiaire du wrapper que l'appelant ne peut pas effectuer lui\-même. Toute opération impliquant une vérification de sécurité limitée représente un danger particulier contrairement à l'obligation d'effectuer un parcours de pile complet. Dans le cadre de vérifications de niveau unique, l'interposition du code wrapper entre l'appelant réel et l'élément d'API dont il est question peut amener facilement la vérification de sécurité à aboutir quand elle ne le devrait pas, ce qui affaiblit la sécurité.  
  
> [!CAUTION]
>  Sécurité d'accès du code et code d'un niveau de confiance partiel  
>   
>  Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code \(CAS\) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.  La sécurité d'accès du code dans .NET Framework ne doit pas être utilisée comme limite de sécurité avec du code d'un niveau de confiance partiel, notamment du code d'origine inconnue. Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité.  
>   
>  Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.  
  
## Délégués  
 La sécurité de délégué diffère selon les versions du .NET Framework.  Cette section décrit les différents comportements de délégué et les considérations sur la sécurité associées.  
  
### Dans les versions 1.0 et 1.1 du .NET Framework  
 Les versions 1.0 et 1.1 du .NET Framework exécutent les actions de sécurité suivantes sur un créateur de délégués et un appelant de délégués.  
  
-   Quand un délégué est créé, des demandes de liaison de sécurité sur la méthode cible du délégué sont exécutées sur le jeu d'autorisations du créateur de délégués.  Si la satisfaction de l'action de sécurité échoue, une <xref:System.Security.SecurityException> est levée.  
  
-   Quand le délégué est appelé, toutes les demandes de sécurité existantes sur l'appelant de délégués sont exécutées.  
  
 Chaque fois que votre code prend un <xref:System.Delegate> à partir de code d'un niveau de confiance moindre et susceptible de l'appeler, veillez à ne pas permettre au code d'un niveau de confiance moindre d'élargir ses autorisations. Si vous prenez un délégué et que vous l'utilisez ultérieurement, le code qui a créé le délégué ne se trouve pas dans la pile des appels et ses autorisations ne seront pas testées si le code dans ou sous le délégué tente une opération protégée. Si votre code et le code de l'appelant disposent de privilèges supérieurs à ceux du créateur, ce dernier peut gérer le chemin d'appel sans faire partie de la pile des appels.  
  
### Dans la version 2.0 du .NET Framework et les versions ultérieures  
 Contrairement aux versions antérieures, la version 2.0 du .NET Framework exécute l'action de sécurité sur le créateur de délégués quand le délégué est créé et appelé.  
  
-   Quand un délégué est créé, des demandes de liaison de sécurité sur la méthode cible du délégué sont exécutées sur le jeu d'autorisations du créateur de délégués.  Si la satisfaction de l'action de sécurité échoue, une <xref:System.Security.SecurityException> est levée.  
  
-   Le jeu d'autorisations du créateur de délégués est également capturé au cours de la création du délégué et stocké avec celui\-ci.  
  
-   Quand le délégué est appelé, le jeu d'autorisations capturé du créateur de délégués est d'abord évalué par rapport à toutes les demandes dans le contexte actuel, si le créateur et l'appelant de délégués appartiennent à des assemblys différents.  Ensuite, toutes les demandes de sécurité existantes sur l'appelant de délégués sont exécutées.  
  
## Demandes de liaison et wrappers  
 Un cas de protection particulier avec des demandes de liaison a fait l'objet d'une consolidation dans l'infrastructure de sécurité, mais il représente toujours une source de failles possibles dans votre code.  
  
 Si du code d'un niveau de confiance suffisant appelle une propriété, un événement ou une méthode par un [LinkDemand](../../../docs/framework/misc/link-demands.md), l'appel aboutit si la vérification d'autorisation **LinkDemand** pour l'appelant est satisfaite. De plus, si le code d'un niveau de confiance suffisant expose une classe qui prend le nom d'une propriété et appelle son accesseur **get** à l'aide de la réflexion, cet appel à l'accesseur **get** aboutit même si le code utilisateur n'a pas le droit d'accéder à cette propriété. Cela tient au fait que **LinkDemand** contrôle uniquement l'appelant immédiat qui correspond au code d'un niveau de confiance suffisant. Essentiellement, le code d'un niveau de confiance suffisant effectue un appel privilégié pour le compte du code utilisateur sans s'assurer que celui\-ci a le droit d'effectuer cet appel.  
  
 Pour éviter de telles brèches dans la sécurité, le Common Language Runtime élargit le contrôle sous la forme d'une demande de parcours de pile complet sur n'importe quel appel indirect à une méthode, constructeur, propriété ou événement protégé par **LinkDemand**. Cette protection entraîne des coûts de performance et change la sémantique de la vérification de sécurité ; la demande de parcours de pile complet risque d'échouer là où la vérification de niveau unique plus rapide aurait réussi.  
  
> [!NOTE]
>  Dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], le code d'un niveau de confiance partiel a été redéfini comme code transparent. Le modèle de transparence dresse une barrière entre le code qui peut effectuer des actions privilégiées \(code critique\), notamment appeler le code natif, et le code qui ne le peut pas \(code transparent\). La transparence remplace l'utilisation du <xref:System.Security.Permissions.SecurityAction> pour la confiance totale pour identifier le code d'un niveau de confiance suffisant avec le <xref:System.Security.SecurityCriticalAttribute>. Pour plus d’informations sur ce point et sur d’autres changements, consultez [Modifications de sécurité](../../../docs/framework/security/security-changes.md).  
  
## Wrappers chargeant des assemblys  
 Plusieurs méthodes utilisées pour charger du code managé, y compris <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>, chargent des assemblys avec la preuve de l'appelant. Si vous encapsulez une de ces méthodes, le système de sécurité peut utiliser l'octroi d'autorisation de votre code à la place des autorisations de l'appelant à votre wrapper afin de charger les assemblys. Vous ne devez pas permettre au code d'un niveau de confiance moindre de charger du code dont les autorisations accordées sont supérieures à celles de l'appelant à votre wrapper.  
  
 Tout code de confiance totale ou dont le niveau de confiance est nettement supérieur à un appelant potentiel \(y compris un appelant avec des autorisations au niveau d'Internet\) risque d'affaiblir la sécurité dans ce contexte. Si votre code possède une méthode publique qui prend un tableau d'octets et le passe à **Assembly.Load** créant ainsi un assembly au nom de l'appelant, il risque de perturber la sécurité.  
  
 Ce problème s'applique aux éléments d'API suivants :  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>  
  
## Demand et LinkDemand  
 La sécurité déclarative propose deux types de vérification de sécurité similaires, mais qui effectuent des vérifications très différentes. Vous devez connaître les deux formes, car un mauvais choix pourrait nuire aux performances et à la sécurité.  
  
 La sécurité déclarative propose les vérifications de sécurité suivantes :  
  
-   <xref:System.Security.Permissions.SecurityAction> spécifie le parcours de pile de sécurité d'accès du code. Tous les appelants sur la pile doivent avoir l'autorisation ou l'identité spécifiée pour passer.**Demand** e produit sur chaque appel, car la pile peut contenir des appelants différents. Si vous appelez une méthode de façon répétée, cette vérification de sécurité se produit à chaque fois.**Demand** constitue une bonne protection contre les attaques malveillantes ; le code non autorisé qui essaye de passer sera détecté.  
  
-   [LinkDemand](../../../docs/framework/misc/link-demands.md) se produit au moment de la compilation juste\-à\-temps \(JIT, Just\-In\-Time\) et vérifie uniquement l'appelant immédiat. Cette vérification de sécurité ne vérifie pas l'appelant de l'appelant. Une fois cette vérification effectuée, il n'y a pas de charge de sécurité supplémentaire, quel que soit le nombre d'appels effectués par l'appelant. Cependant, il n'y a pas non plus de protection contre les attaques malveillantes. Avec **LinkDemand**, tout code qui réussit le test et peut référencer votre code risque de perturber la sécurité en permettant à du code nuisible d'appeler à l'aide du code autorisé. Ainsi, n'utilisez pas **LinkDemand**, sauf s'il est possible d'éviter sans exception toutes les failles possibles.  
  
    > [!NOTE]
    >  Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], les demandes de liaison ont été remplacées par l'attribut <xref:System.Security.SecurityCriticalAttribute> dans les assemblys <xref:System.Security.SecurityRuleSet>. L'attribut <xref:System.Security.SecurityCriticalAttribute> est équivalent à une demande de liaison pour une confiance totale ; toutefois, il affecte également les règles d'héritage. Pour plus d’informations sur ce changement, consultez [Code transparent de sécurité, niveau 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Les précautions supplémentaires requises pendant l'utilisation de **LinkDemand** doivent être programmées individuellement ; le système de sécurité peut aider à leur application. La moindre erreur fait apparaître une défaillance en matière de sécurité. Tout le code autorisé qui utilise votre code doit prendre en charge l'implémentation de la sécurité supplémentaire en effectuant les opérations suivantes :  
  
-   Limiter l'accès du code appelant à la classe ou à l'assembly.  
  
-   Placer les mêmes vérifications de sécurité sur le code appelant que celles figurant dans le code appelé et forcer ses appelants à effectuer les vérifications. Par exemple, si vous écrivez du code qui appelle une méthode protégée par **LinkDemand** pour <xref:System.Security.Permissions.SecurityPermission> avec l’indicateur <xref:System.Security.Permissions.SecurityPermissionFlag>, votre méthode doit également utiliser **LinkDemand** \(ou **Demand**, qui est plus fort\) pour cette autorisation. L'exception : si votre code utilise la méthode protégée par **LinkDemand** d'une façon limitée que vous estimez être sécurisée étant donné les autres mécanismes de protection de la sécurité \(comme les demandes\) présents dans votre code. Dans ce cas exceptionnel, l'appelant prend la responsabilité d'affaiblir la protection de la sécurité sur le code sous\-jacent.  
  
-   Veiller à ce que les appelants de votre code ne puissent pas tromper celui\-ci et lui faire appeler le code protégé de leur part. En d'autres termes, les appelants ne peuvent pas forcer le code autorisé à passer des paramètres spécifiques au code protégé ou pour obtenir de ce dernier des résultats.  
  
### Interfaces et demandes de liaison  
 Si une méthode, propriété ou événement virtuel avec **LinkDemand** substitue une méthode de la classe de base, cette méthode doit également avoir le même **LinkDemand** pour que la méthode substituée soit efficace. Il est possible pour le code nuisible d'effectuer un cast en type de base en retour et d'appeler la méthode de la classe de base. Notez également que les demandes de liaison peuvent être ajoutées implicitement aux assemblys qui n'ont pas l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de niveau assembly.  
  
 Il est recommandé de protéger les implémentations des méthodes avec des demandes de liaison quand des méthodes d'interface possèdent également des demandes de liaison. Notez les informations suivantes concernant l'utilisation de demandes de liaison avec des interfaces :  
  
-   L'attribut **AllowPartiallyTrustedCallersAttribute** s'applique également aux interfaces.  
  
-   Vous pouvez placer des demandes de liaison sur des interfaces pour éviter que des interfaces spécifiques soient utilisées par du code d'un niveau de confiance partiel, comme dans le cas de l'utilisation de l'attribut **AllowPartiallyTrustedCallersAttribute** .  
  
-   Si vous avez une interface définie dans un assembly qui ne contient pas l'attribut **AllowPartiallyTrustedCallersAttribute** , vous pouvez implémenter cette interface sur une classe d'un niveau de confiance partiel.  
  
-   Si vous placez **LinkDemand** sur une méthode publique d'une classe qui implémente une méthode d'interface, **LinkDemand** ne sera pas appliqué si vous effectuez ensuite un cast en interface et appelez la méthode. Dans ce cas, comme vous avez relié à l'interface, seul **LinkDemand** sur l'interface est honoré.  
  
 Passez en revue les éléments suivants en examinant les questions de sécurité :  
  
-   Explicitez les demandes de liaison sur des méthodes d'interface. Veillez à ce que ces demandes de liaison offrent la protection attendue. Déterminez si du code nuisible peut utiliser un cast pour contourner les demandes de liaison comme décrit précédemment.  
  
-   Méthodes virtuelles avec demandes de liaison appliquées.  
  
-   Types et interfaces qu'ils implémentent. Ceux\-ci doivent utiliser les demandes de liaison de manière cohérente.  
  
## Voir aussi  
 [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md)