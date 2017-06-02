---
title: "Proc&#233;dure pas &#224; pas&#160;: &#233;mission de code dans des sc&#233;narios de confiance partielle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthodes dynamiques hébergées de manière anonyme (.NET Framework)"
  - "méthodes dynamiques"
  - "émettre des assemblys dynamiques, scénarios de confiance partielle"
  - "confiance partielle, créer des méthodes dynamiques"
  - "confiance partielle, réflexion"
  - "émission de réflexion, méthodes dynamiques hébergées de manière anonyme"
  - "émission de réflexion, méthodes dynamiques"
  - "émission de réflexion, scénarios de confiance partielle"
ms.assetid: c45be261-2a9d-4c4e-9bd6-27f0931b7d25
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Proc&#233;dure pas &#224; pas&#160;: &#233;mission de code dans des sc&#233;narios de confiance partielle
L'émission de réflexion utilise le même jeu d'API dans les cas de confiance totale ou partielle, mais certaines fonctionnalités requièrent des autorisations spéciales dans le code d'un niveau de confiance partiel.  De plus, l'émission de réflexion a une fonctionnalité, méthodes dynamiques hébergées de manière anonyme, qui est destinée à être utilisée avec la confiance partielle et par les assemblys Security Transparent.  
  
> [!NOTE]
>  Avant [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)], l'émission de code est requise <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>.  Cette autorisation est incluse par défaut dans les jeux d'autorisations nommés `FullTrust` et `Intranet`, mais pas dans le jeu d'autorisations `Internet`.  Par conséquent, une bibliothèque pourrait être utilisée avec une confiance partielle uniquement si elle avait l'attribut <xref:System.Security.SecurityCriticalAttribute> et si elle exécute une méthode <xref:System.Security.PermissionSet.Assert%2A> pour <xref:System.Security.Permissions.ReflectionPermissionFlag>.  Ces bibliothèques nécessitent une révision de sécurité approfondie car les erreurs de codage pourraient provoquer des failles de sécurité.  [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] autorise l'émission de code dans des scénarios de confiance partielle sans émission de demandes de sécurité, parce que la génération du code n'est pas fondamentalement une opération privilégiée.  Autrement dit, le code généré n'a pas plus d'autorisations que l'assembly qui l'émet.  Cela permet aux bibliothèques qui émettent du code d'être Security Transparent et évite d'avoir à déclarer <xref:System.Security.Permissions.ReflectionPermissionFlag>, de sorte que l'écriture d'une bibliothèque sécurisée ne nécessite pas de révision de sécurité approfondie.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   [Installation d'un bac à sable \(sandbox\) simple pour le test de code d'un niveau de confiance partiel](#Setting_up).  
  
    > [!IMPORTANT]
    >  Il s'agit d'une méthode simple pour expérimenter du code avec un niveau de confiance partiel.  Pour exécuter du code qui provient réellement d'emplacements non fiable, consultez [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
-   [Exécution du code dans les domaines d'application de confiance partielle](#Running_code).  
  
-   [Utilisation de méthodes dynamiques hébergées de manière anonyme pour émettre et exécuter du code de confiance partielle](#Using_methods).  
  
 Pour plus d'informations sur l'émission du code dans les scénarios de confiance partielle, consultez [Problèmes de sécurité dans l'émission de réflexion](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md).  
  
 Pour obtenir la liste complète du code utilisé dans ces procédures, consultez la [section Exemple](#Example) à la fin de cette procédure pas à pas.  
  
<a name="Setting_up"></a>   
## Installation d'emplacements de confiance partielle  
 Les deux procédures suivantes indiquent comment installer des emplacements à partir desquels vous pouvez tester du code avec un niveau de confiance partiel.  
  
-   La première procédure explique comment créer un domaine d'application sandbox dans lequel le code bénéficie d'autorisations Internet.  
  
-   La deuxième procédure indique comment ajouter <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> à un domaine d'application partiellement fiable, pour permettre l'accès à des données privées dans des assemblys de confiance égale ou inférieure.  
  
### Création de domaines d'application en bac à sable \(Sandboxed\)  
 Pour créer un domaine d'application dans lequel vos assemblys s'exécutent avec la confiance partielle, vous devez spécifier le jeu d'autorisations à accorder aux assemblys en utilisant la surcharge de méthode [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> pour créer le domaine d'application.  Pour spécifier le jeu d'autorisations, le plus simple est de récupérer un jeu d'autorisations nommé à partir de la stratégie de sécurité.  
  
 La procédure suivante crée un domaine d'application en bac à sable \(sandbox\) qui exécute votre code avec une confiance partielle, afin de tester des scénarios dans lesquels le code émis peut accéder uniquement aux membres publics des types publics.  Une procédure suivante montre comment ajouter <xref:System.Security.Permissions.ReflectionPermissionFlag>, afin de tester des scénarios dans lesquels le code émis peut accéder aux types non public et aux membres dans les assemblys bénéficiant d'autorisations égales ou moindres.  
  
##### Pour créer un domaine d'application avec une confiance partielle  
  
1.  Créez un jeu d'autorisations à accorder aux assemblys dans le domaine d'application sandbox.  Dans ce cas, le jeu d'autorisations de la zone Internet est utilisé.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#2)]
     [!code-vb[HowToEmitCodeInPartialTrust#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#2)]  
  
2.  Créez un objet <xref:System.AppDomainSetup> pour initialiser le domaine d'application avec un chemin d'accès d'application.  
  
    > [!IMPORTANT]
    >  Pour des raisons de simplicité, cet exemple de code utilise le dossier actif.  Pour exécuter du code qui provient réellement d'Internet, utilisez un dossier séparé pour le code non fiable, comme décrit dans [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#3)]
     [!code-vb[HowToEmitCodeInPartialTrust#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#3)]  
  
3.  Créez le domaine d'application, en spécifiant les informations d'installation du domaine d'application et le jeu d'autorisations pour tous les assemblys exécutés dans le domaine d'application.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#5)]
     [!code-vb[HowToEmitCodeInPartialTrust#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#5)]  
  
     Le dernier paramètre de la surcharge de méthode [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> vous permet de spécifier un jeu des assemblys qui bénéficient de la confiance totale, à la place du jeu d'autorisations du domaine d'application.  Vous n'avez pas à spécifier les assemblys [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] que votre application utilise, parce que ces assemblys sont dans le Global Assembly Cache.  Les assemblys dans le Global Assembly Cache ont toujours un niveau de confiance total.  Vous pouvez utiliser ce paramètre pour spécifier des assemblys avec nom fort qui ne sont pas dans le Global Assembly Cache.  
  
### Ajout de RestrictedMemberAccess aux domaines en bac à sable \(sandbox\)  
 Les applications hôtes peuvent permettre aux méthodes dynamiques hébergées de manière anonyme d'avoir accès aux données privées dans les assemblys bénéficiant de niveaux de confiance inférieurs ou égaux au niveau de confiance de l'assembly qui émet le code.  Pour permettre à cette capacité limitée d'ignorer les vérifications de visibilité JIT \(juste\-à\-temps\), l'application hôte ajoute un objet <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> \(RMA\) au jeu d'autorisations.  
  
 Par exemple, un hôte peut accorder des autorisations Internet aux applications Internet plus RMA, afin qu'une application Internet puisse émettre du code qui accède aux données privées dans ses propres assemblys.  Dans la mesure où l'accès est limité aux assemblys de confiance inférieure ou égale une application Internet ne peut pas accéder aux membres d'assemblys d'un niveau de confiance total tels que les assemblys [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  Pour empêcher l'élévation de privilège, des informations de la pile pour l'assembly émetteur sont incluses lorsque des méthodes dynamiques hébergées de manière anonyme sont construites.  Lorsque la méthode est appelée, les informations de la pile sont vérifiées.  Ainsi, une méthode dynamique hébergée de manière anonyme qui est appelée à partir d'un code de niveau de confiance total est encore limitée au niveau de confiance de l'assembly émetteur.  
  
##### Pour créer un domaine d'application avec une confiance partielle plus RMA  
  
1.  Créez un objet <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag> \(RMA\) et utilisez la méthode <xref:System.Security.PermissionSet.SetPermission%2A?displayProperty=fullName> pour ajouter l'autorisation au jeu d'autorisations.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#7)]
     [!code-vb[HowToEmitCodeInPartialTrust#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#7)]  
  
     La méthode <xref:System.Security.PermissionSet.AddPermission%2A> ajoute l'autorisation au jeu d'autorisations, si ce n'est déjà fait.  Si l'autorisation est déjà incluse dans le jeu d'autorisations, les indicateurs spécifiés sont ajoutés à l'autorisation existante.  
  
    > [!NOTE]
    >  RMA est une fonctionnalité de méthodes dynamiques hébergées de manière anonyme.  Lorsque les méthodes dynamiques ordinaires ignorent les contrôles de visibilité JIT, le code émis nécessite une confiance totale.  
  
2.  Créez le domaine d'application, en spécifiant les informations d'installation du domaine d'application et le jeu d'autorisations.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#8)]
     [!code-vb[HowToEmitCodeInPartialTrust#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#8)]  
  
<a name="Running_code"></a>   
## Exécution du code dans des domaines d'application en bac de sable \(sandbox\)  
 La procédure suivante explique comment définir une classe en utilisant des méthodes qui peuvent être exécutées dans un domaine d'application, comment créer une instance de la classe dans le domaine, et comment exécuter ses méthodes.  
  
#### Pour définir et exécuter une méthode dans un domaine d'application  
  
1.  Définissez une classe qui dérive de <xref:System.MarshalByRefObject>.  Cela vous permet de créer des instances de la classe dans d'autres domaines d'application et faire des appels de méthode au\-delà des limites de domaine d'application.  Dans cet exemple, la classe s'appelle `Worker`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#10)]
     [!code-vb[HowToEmitCodeInPartialTrust#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#10)]  
  
2.  Définissez une méthode publique qui contient le code à exécuter.  Dans cet exemple, le code émet une méthode dynamique simple, crée un délégué pour exécuter la méthode et appelle le délégué.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#11)]
     [!code-vb[HowToEmitCodeInPartialTrust#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#11)]  
  
3.  Dans votre programme principal, obtenez le nom complet de votre assembly.  Ce nom est utilisé lorsque vous créez des instances de la classe `Worker` dans le domaine d'application en bac à sable \(sandbox\).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#14)]
     [!code-vb[HowToEmitCodeInPartialTrust#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#14)]  
  
4.  Dans votre programme principal, créez un domaine d'application en bac à sable \(sandbox\), comme décrit dans [la première procédure](#Setting_up) de cette procédure pas à pas.  Vous n'avez à ajouter aucune autorisation au jeu d'autorisations `Internet`, parce que la méthode `SimpleEmitDemo` utilise des méthodes publiques uniquement.  
  
5.  Dans votre programme principal, créez une instance de la classe `Worker` dans le domaine d'application en bac à sable \(sandbox\).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#12)]
     [!code-vb[HowToEmitCodeInPartialTrust#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#12)]  
  
     La méthode <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> crée l'objet dans le domaine d'application cible et retourne un proxy qui peut être utilisé pour appeler les propriétés et méthodes de l'objet.  
  
    > [!NOTE]
    >  Si vous utilisez ce code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vous devez changer le nombre de la classe qui inclue l'espace de noms.  Par défaut, l'espace de noms est le nom du projet.  Par exemple, si le projet est « PartialTrust », le nom de classe doit être « PartialTrust.Worker ».  
  
6.  Ajoutez du code pour appeler la méthode `SimpleEmitDemo`.  L'appel est marshalé à travers la limite du domaine d'application, et le code est exécuté dans le domaine d'application placée en bac à sable \(sandbox\).  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#13)]
     [!code-vb[HowToEmitCodeInPartialTrust#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#13)]  
  
<a name="Using_methods"></a>   
## Utilisation des méthodes dynamiques hébergées de manière anonyme  
 Les méthodes dynamiques hébergées de manière anonyme sont associées à un assembly transparent fourni par le système.  Par conséquent, le code qu'elles contiennent est transparent.  Les méthodes dynamiques ordinaires, en revanche, doivent être associées à un module existant \(directement spécifié ou déduit d'un type associé\) et dérivent leur niveau de sécurité de ce module.  
  
> [!NOTE]
>  La seule méthode pour associer une méthode dynamique à l'assembly qui fournit l'hébergement anonyme est d'utiliser les constructeurs décrits dans la procédure suivante.  Vous ne pouvez pas spécifier explicitement de module dans l'assembly d'hébergement anonyme.  
  
 Les méthodes dynamiques ordinaires ont accès aux membres internes du module auquel elles sont associées, ou aux membres privés du type auquel elles sont associées.  Dans la mesure où les méthodes dynamiques hébergées de manière anonyme sont isolées du reste du code, elles n'ont pas accès aux données privées.  Toutefois, elles ont une capacité restreinte d'ignorer les vérifications de visibilité JIT pour accéder aux données privées.  Cette capacité est limitée aux assemblys qui ont des niveaux de confiance inférieure ou égaux au niveau de confiance de l'assembly qui émet le code.  
  
 Pour empêcher l'élévation de privilège, des informations de la pile pour l'assembly émetteur sont incluses lorsque des méthodes dynamiques hébergées de manière anonyme sont construites.  Lorsque la méthode est appelée, les informations de la pile sont vérifiées.  Une méthode dynamique hébergée de manière anonyme qui est appelée à partir d'un code de niveau de confiance total est encore limitée au niveau de confiance de l'assembly à l'origine de son émission.  
  
#### Pour utiliser des méthodes dynamiques hébergées de manière anonyme  
  
-   Créez une méthode dynamique hébergée de manière anonyme en utilisant un constructeur qui ne spécifie pas un module associé ou type.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#15)]
     [!code-vb[HowToEmitCodeInPartialTrust#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#15)]  
  
     Si une méthode dynamique hébergée de manière anonyme utilise uniquement des types publics et des méthodes, elle ne requiert pas d'accès de membre restreint et n'a pas à ignorer les contrôles de visibilité JIT.  
  
     Aucune autorisation spéciale n'est requise pour émettre une méthode dynamique, mais le code émis requiert les autorisations demandées par les types et méthodes qu'il utilise.  Par exemple, si le code émis appelle une méthode qui accède à un fichier, il requiert <xref:System.Security.Permissions.FileIOPermission>.  Si le niveau de confiance n'inclut pas cette autorisation, une exception de sécurité est levée lorsque le code émis est exécuté.  Le code montré ici émet une méthode dynamique qui utilise uniquement la méthode <xref:System.Console.WriteLine%2A?displayProperty=fullName>.  Par conséquent, le code peut être exécuté à partir d'emplacements de confiance partielle.  
  
-   Ou bien, créez une méthode dynamique hébergée de manière anonyme avec capacité restreinte pour ignorer les contrôles de visibilité JIT, en utilisant le constructeur [DynamicMethod\(String, Type, Type\<xref:System.Reflection.Emit.DynamicMethod.%23ctor%28System.String%2CSystem.Type%2CSystem.Type%5B%5D%2CSystem.Boolean%29> et en spécifiant `true` pour le paramètre `restrictedSkipVisibility`.  
  
     [!code-csharp[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#16)]
     [!code-vb[HowToEmitCodeInPartialTrust#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#16)]  
  
     La restriction est que la méthode dynamique hébergée de manière anonyme peut accéder uniquement aux données privées dans les assemblys avec des niveaux de confiance inférieurs ou égaux au niveau de confiance de l'assembly d'émission.  Par exemple, si la méthode dynamique s'exécute avec l'approbation Internet, elle peut accéder aux données privées d'autres assemblys également exécutés avec l'approbation Internet, mais elle ne peut pas accéder aux données privées d'assemblys [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  Les assemblys [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sont installés dans le Global Assembly Cache et présentent toujours un niveau de confiance totale.  
  
     Les méthodes dynamiques hébergées de manière anonyme peuvent utiliser cette capacité restreinte pour ignorer les vérifications de visibilité JIT uniquement si l'application hôte accorde <xref:System.Security.Permissions.ReflectionPermission> avec l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName>.  La demande pour cette autorisation est faite lorsque la méthode est appelée.  
  
    > [!NOTE]
    >  Les informations de la pile d'appel pour l'assembly d'émission sont incluses lors de la construction de la méthode dynamique.  Par conséquent, la demande est faite par rapport aux autorisations de l'assembly d'émission et non de l'assembly qui appelle la méthode.  Cela empêche l'exécution du code émis avec des autorisations élevées.  
  
     L'[exemple de code complet](#Example) à la fin de cette procédure pas à pas illustre l'utilisation et les limitations d'accès de membre restreint.  Sa classe `Worker` inclut une méthode qui peut créer des méthodes dynamiques hébergées de manière anonyme avec ou sans la capacité restreinte d'ignorer les contrôles de visibilité, et l'exemple montre le résultat de l'exécution de cette méthode dans les domaines d'application qui ont des niveaux de confiance différents.  
  
    > [!NOTE]
    >  La capacité restreinte d'ignorer les contrôles de visibilité est une caractéristique des méthodes dynamiques hébergées de manière anonyme.  Lorsque les méthodes dynamiques ordinaires ignorent les contrôles de visibilité JIT, elles doivent se voir accorder une confiance totale.  
  
<a name="Example"></a>   
## Exemple  
  
### Description  
 L'exemple de code suivant montre l'utilisation de l'indicateur <xref:System.Security.Permissions.ReflectionPermissionFlag> pour permettre aux méthodes dynamiques hébergées de manière anonyme d'ignorer les contrôles de visibilité JIT, mais uniquement lorsque le membre cible a un niveau de confiance inférieur ou égal à celui de l'assembly qui émet le code.  
  
 L'exemple définit une classe `Worker` qui peut être marshalée au\-delà des limites du domaine d'application.  La classe a deux surcharges de méthode `AccessPrivateMethod` qui émettent et exécutent des méthodes dynamiques.  La première surcharge émet une méthode dynamique qui appelle la méthode `PrivateMethod` privée de la classe `Worker`, et elle peut émettre la méthode dynamique avec ou sans contrôles de visibilité JIT.  La seconde surcharge émet une méthode dynamique qui accède à une propriété `internal` \(propriété`Friend` dans Visual Basic\) de la classe <xref:System.String>.  
  
 L'exemple utilise une méthode d'assistance pour créer un jeu d'autorisations limité aux autorisations `Internet`, puis crée un domaine d'application, en utilisant la surcharge de méthode [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> pour spécifier que tout le code qui s'exécute dans ce domaine utilise ce jeu d'autorisations.  L'exemple crée une instance de la classe `Worker` dans le domaine d'application et exécute la méthode `AccessPrivateMethod` deux fois.  
  
-   La première fois que la méthode `AccessPrivateMethod` est exécutée, les contrôles de visibilité JIT sont appliqués.  La méthode dynamique échoue lorsqu'elle est appelée, parce que les contrôles de visibilité JIT l'empêchent d'accéder à la méthode privée.  
  
-   La seconde fois que la méthode `AccessPrivateMethod` est exécutée, les contrôles de visibilité JIT sont ignorés.  La méthode dynamique échoue lors de la compilation, parce que le jeu d'autorisations `Internet` n'accorde pas d'autorisations suffisantes pour ignorer les contrôles de visibilité.  
  
 L'exemple ajoute <xref:System.Security.Permissions.ReflectionPermission> avec <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> au jeu d'autorisations.  L'exemple crée ensuite un deuxième domaine, en spécifiant que les autorisations du nouveau jeu d'autorisations sont accordées à l'ensemble du code qui s'exécute dans le domaine.  L'exemple crée une instance de la classe `Worker` dans le nouveau domaine d'application et exécute les deux surcharges de la méthode `AccessPrivateMethod`.  
  
-   La première surcharge de la méthode `AccessPrivateMethod` est exécutée et les contrôles de visibilité JIT sont ignorés.  La méthode dynamique est compilée et exécutée avec succès, parce que l'assembly qui émet le code est le même que l'assembly qui contient la méthode privée.  Par conséquent, les niveaux de confiance sont égaux.  Si l'application qui contient la classe `Worker` avait plusieurs assemblys, le même processus réussirait pour chacun de ces assemblys, parce qu'ils seraient tous au même niveau de confiance.  
  
-   La seconde surcharge de la méthode `AccessPrivateMethod` est exécutée et les contrôles de visibilité JIT sont à nouveau ignorés.  Cette fois\-ci, la méthode dynamique échoue lors de la compilation, parce qu'elle essaie d'accéder à la propriété `internal` `FirstChar` de la classe <xref:System.String>.  L'assembly qui contient la classe <xref:System.String> est d'un niveau de confiance suffisant.  Par conséquent, il s'agit d'un niveau de confiance supérieur à celui de l'assembly qui émet le code.  
  
 Cette comparaison montre comment <xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=fullName> permet à un code de niveau de confiance partiel d'ignorer les contrôles de visibilité pour un autre code de niveau de confiance partiel sans compromettre la sécurité du code de confiance.  
  
### Code  
 [!code-csharp[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/cs/source.cs#1)]
 [!code-vb[HowToEmitCodeInPartialTrust#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToEmitCodeInPartialTrust/vb/source.vb#1)]  
  
## Compilation du code  
  
-   Si vous générez cet exemple de code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vous devez modifier le nom de la classe pour inclure l'espace de noms lorsque vous le passez à la méthode <xref:System.AppDomain.CreateInstanceAndUnwrap%2A>.  Par défaut, l'espace de noms est le nom du projet.  Par exemple, si le projet est « PartialTrust », le nom de classe doit être « PartialTrust.Worker ».  
  
## Voir aussi  
 [Problèmes de sécurité dans l'émission de réflexion](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)   
 [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)