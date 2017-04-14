---
title: "Concepts fondamentaux sur la s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "autorisations (.NET Framework)"
  - "sécurité (.NET Framework), à propos de la sécurité"
  - "accès non autorisé"
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: 22
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 20
---
# Concepts fondamentaux sur la s&#233;curit&#233;
Le Microsoft .NET Framework offre la transparence de la sécurité, la sécurité d'accès du code et la sécurité basée sur les rôles pour aider à résoudre les problèmes de sécurité relatifs au code mobile et pour permettre aux composants de déterminer ce que les utilisateurs sont autorisés à faire.  Ces mécanismes de sécurité reposent sur un modèle simple et cohérent qui permet aux développeurs familiarisés avec la sécurité d'accès du code d'utiliser facilement la sécurité basée sur les rôles et vice versa.  La sécurité d'accès du code et la sécurité basée sur les rôles sont implémentées à l'aide d'une infrastructure commune fournie par le Common Language Runtime.  
  
> [!NOTE]
>  À compter du [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la transparence de la sécurité est le mécanisme d'application par défaut.  La transparence de la sécurité sépare le code qui s'exécute dans le cadre de l'application du code qui s'exécute dans le cadre de l'infrastructure.  Pour plus d'informations, consultez [Code transparent de sécurité \(security\-transparent\)](../../../docs/framework/misc/security-transparent-code.md).  
  
 Comme ils utilisent les mêmes modèle et infrastructure, la sécurité d'accès du code et la sécurité basée sur les rôles partagent plusieurs concepts sous\-jacents, qui sont décrits dans cette section.  Assurez\-vous que vous êtes familiarisé avec ces concepts avant de lire la documentation sur la sécurité d'accès du code et la sécurité basée sur les rôles .NET Framework.  
  
## Autorisations de sécurité  
 Le Common Language Runtime permet au code d'effectuer uniquement les opérations qu'il est autorisé à exécuter.  Le runtime utilise des objets appelés autorisations pour appliquer des restrictions sur du code managé.  Le runtime fournit des classes d'autorisations intégrées dans plusieurs espaces de noms et prend également en charge la conception et l'implémentation de classes d'autorisations personnalisées.  
  
 Il existe deux types d'autorisations, ayant chacun une finalité spécifique :  
  
-   Les autorisations d'accès de code représentent l'accès à une ressource protégée ou la possibilité d'effectuer une opération protégée.  
  
-   Les autorisations de sécurité basées sur les rôles fournissent un mécanisme permettant de savoir si un utilisateur \(ou l'agent qui agit en son nom\) possède une identité particulière ou est membre d'un rôle spécifié.  <xref:System.Security.Permissions.PrincipalPermission> est la seule autorisation de sécurité basée sur les rôles.  
  
 Les autorisations de sécurité peuvent se présenter sous la forme d'une classe d'autorisation \(sécurité impérative\) ou d'un attribut qui représente une classe d'autorisation \(sécurité déclarative\).  La classe de base pour les autorisations de sécurité est <xref:System.Security.CodeAccessPermission?displayProperty=fullName>, tandis que la classe de base pour les attributs d'autorisation de sécurité est <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>.  
  
 Une application, sous la forme d'un assembly, se voit accorder un jeu d'autorisations au moment où elle est chargée dans un domaine d'application.  L'attribution est généralement effectuée à l'aide de jeux d'autorisations prédéfinis déterminés par la méthode <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=fullName>.  Le jeu d'autorisations détermine les autorisations dont dispose le code.  Le runtime accorde des autorisations en fonction de l'emplacement d'origine du code \(par exemple, l'ordinateur local, l'intranet local ou Internet\).  Des autorisations spéciales peuvent également être accordées au code s'il est chargé dans un bac à sable \(sandbox\).  Pour plus d'informations sur l'exécution de code dans un bac à sable \(sandbox\), consultez [Comment : exécuter du code d'un niveau de confiance partiel dans un bac à sable \(sandbox\)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Les principales utilisations des autorisations sont les suivantes :  
  
-   Le code de bibliothèque peut demander que ses appelants possèdent des autorisations spécifiques.  Si vous placez une demande <xref:System.Security.CodeAccessPermission.Demand%2A> pour une autorisation dans votre code, tout code utilisant ce dernier doit avoir cette autorisation pour s'exécuter.  Les demandes permettent de déterminer si les appelants ont accès à des ressources spécifiques ou de découvrir l'identité d'un appelant.  
  
-   Le code peut utiliser des autorisations pour refuser l'accès aux ressources qu'il souhaite protéger.  Vous pouvez utiliser <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> pour spécifier un jeu d'autorisations limité, refusant implicitement toutes les autres autorisations.  Toutefois, nous vous déconseillons d'utiliser <xref:System.Security.Permissions.SecurityAction> pour interdire l'accès dans le but de protéger le code contre toute utilisation malveillante.  Les assemblys appelés, dont le jeu d'autorisations comporte les autorisations implicitement refusées, peuvent remplacer les autorisations refusées en effectuant un <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> pour toute autorisation qu'ils souhaitent utiliser.  Par exemple, si vous avez uniquement autorisé <xref:System.Security.Permissions.UIPermission> et appelé un assembly qui, par nature, comporte <xref:System.Security.Permissions.FileIOPermission>, l'assembly peut simplement effectuer une <xref:System.Security.Permissions.SecurityAction> pour <xref:System.Security.Permissions.FileIOPermission> et effectuer des opérations sur les fichiers.  La seule méthode permettant de protéger efficacement les ressources contre le code non fiable dans les assemblys référencés consiste à exécuter ce code avec un jeu d'autorisations qui n'inclut pas ces autorisations.  
  
### Autorisations d'accès du code  
 Les autorisations d'accès du code sont des objets d'autorisation qui permettent de protéger les ressources et les opérations de toute utilisation non autorisée.  Elles constituent un élément fondamental du mécanisme utilisé par le Common Language Runtime pour imposer des restrictions de sécurité sur le code managé.  
  
 Chaque autorisation d'accès du code représente l'un des droits suivants :  
  
-   Le droit d'accéder à des ressources protégées, telles que des fichiers ou des variables d'environnement  
  
-   Le droit d'exécuter une opération protégée, telle que l'accès à du code non managé  
  
 Le code peut demander ou exiger toutes les autorisations d'accès, puis le runtime décide lesquelles accorder, le cas échéant.  
  
 Chaque autorisation d'accès du code est dérivée de la classe <xref:System.Security.CodeAccessPermission>, ce qui signifie que toutes les autorisations d'accès du code ont des méthodes en commun, notamment **Demand**, **Assert**, **Deny**, **PermitOnly**, **IsSubsetOf**, **Intersect** et **Union**.  
  
> [!IMPORTANT]
>  Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la prise en charge du runtime a été supprimée afin d'appliquer les demandes d'autorisation <xref:System.Security.Permissions.SecurityAction>, <xref:System.Security.Permissions.SecurityAction>, <xref:System.Security.Permissions.SecurityAction> et <xref:System.Security.Permissions.SecurityAction>.  Ces demandes ne devraient pas être utilisées dans le code qui est basé sur le [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ou version ultérieure.  Pour plus d'informations sur cette modification et d'autres modifications, consultez [Modifications de sécurité](../../../docs/framework/security/security-changes.md).  
  
### Autorisations de sécurité basées sur les rôles  
 <xref:System.Security.Permissions.PrincipalPermission> est une autorisation de sécurité basée sur les rôles qui permet de déterminer si l'utilisateur a une identité spécifique ou s'il est membre d'un rôle particulier.  **PrincipalPermission** est la seule autorisation de sécurité basée sur les rôles fournie par la bibliothèque de classes .NET Framework.  
  
## Sécurité de type et sécurité  
 Le code de type sécurisé accède uniquement aux emplacements de mémoire auxquels il est autorisé à accéder.  \(Dans le cadre de cette présentation, la sécurité de type fait spécifiquement référence à la sécurité de type de la mémoire et ne doit pas être confondue avec la sécurité de type dans un contexte plus large.\) Par exemple, le code de type sécurisé ne peut pas lire les valeurs des champs privés d'un autre objet.  Il accède aux types uniquement de manière autorisée et bien définie.  
  
 Pendant la compilation juste\-à\-temps \(JIT, Just\-In\-Time\), un processus de vérification facultatif examine les métadonnées et le Microsoft Intermediate Language \(MSIL\) d'une méthode devant subir une compilation JIT en code machine natif pour vérifier qu'ils sont de type sécurisé.  Ce processus est omis si le code est autorisé à ignorer la vérification.  Pour plus d'informations sur la vérification, consultez [Processus d'exécution managée](../../../docs/standard/managed-execution-process.md).  
  
 Bien que la vérification de sécurité de type ne soit pas obligatoire pour exécuter du code managé, la sécurité de type joue un rôle crucial dans l'isolation des assemblys et dans la mise en œuvre de la sécurité.  Quand le code est de type sécurisé, le Common Language Runtime peut isoler totalement les assemblys les uns des autres.  Cette isolation permet de s'assurer que les assemblys ne peuvent pas nuire les uns aux autres et augmente la fiabilité des applications.  Les composants de type sécurisé peuvent s'exécuter en toute sécurité dans le même processus, même s'ils sont approuvés à différents niveaux.  Quand le code n'est pas de type sécurisé, des effets secondaires indésirables peuvent se produire.  Par exemple, le runtime ne peut pas empêcher du code managé d'appeler du code natif \(non managé\) et d'exécuter des opérations nuisibles.  Quand le code est de type sécurisé, le mécanisme de sécurité du runtime garantit qu'il n'accède pas à du code natif, sauf s'il a l'autorisation de le faire.  Tout le code qui n'est pas de type sécurisé ne peut s'exécuter que s'il a obtenu l'autorisation <xref:System.Security.Permissions.SecurityPermission> avec le membre d'énumération transmis <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>.  
  
 Pour plus d'informations, consultez [NIB: Writing Verifiably Type\-Safe Code](http://msdn.microsoft.com/fr-fr/d18f10ef-3b48-4f47-8726-96714021547b).  
  
## Principal  
 Un principal représente l'identité et le rôle d'un utilisateur et agit au nom de l'utilisateur.  Dans .NET Framework, la sécurité basée sur les rôles prend en charge trois types de principaux :  
  
-   Les principaux génériques représentent les utilisateurs et les rôles qui existent indépendamment des utilisateurs et des rôles Windows.  
  
-   Les principaux Windows représentent les utilisateurs et les rôles Windows \(ou leurs groupes Windows\).  Un principal Windows peut emprunter l'identité d'un autre utilisateur, ce qui signifie qu'il peut accéder à une ressource sous le nom d'un utilisateur tout en présentant l'identité de l'autre utilisateur.  
  
-   Les principaux personnalisés peuvent être définis par une application, en fonction des besoins de celle\-ci.  Ils peuvent étendre les notions de base applicables à l'identité et aux rôles du principal.  
  
 Pour plus d'informations, consultez [Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## Authentification  
 Le processus d'authentification consiste à établir et à vérifier l'identité d'un principal en examinant les informations d'identification de l'utilisateur et en les validant auprès de l'autorité appropriée.  Votre code peut utiliser directement les informations obtenues au cours de l'authentification.  Vous pouvez également utiliser la sécurité basée sur les rôles du .NET Framework pour authentifier l'utilisateur actuel et déterminer s'il faut ou non autoriser ce principal à accéder à votre code.  Consultez les surcharges de la méthode <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=fullName> pour obtenir des exemples d'authentification du principal pour des rôles spécifiques.  Par exemple, vous pouvez utiliser la surcharge <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=fullName> pour déterminer si l'utilisateur actuel est membre du groupe Administrateurs.  
  
 De nombreux mécanismes d'authentification sont utilisés de nos jours et la majorité d'entre eux peuvent être utilisés avec la sécurité basée sur les rôles de .NET Framework.  Parmi les mécanismes les plus courants figurent notamment Basic, Digest, Passport, les mécanismes liés aux systèmes d'exploitation \(tels que NTLM ou Kerberos\) ou encore ceux définis par les applications.  
  
### Exemple  
 L'exemple suivant nécessite que le principal actif soit un administrateur.  Le paramètre `name` est `null`, qui autorise tout utilisateur ayant la qualité d'administrateur à passer la demande.  
  
> [!NOTE]
>  Dans Windows Vista, le contrôle de compte d'utilisateur détermine les privilèges d'un utilisateur.  Si vous êtes membre du groupe Administrateurs intégrés, deux jetons d'accès au moment de l'exécution vous sont assignés : un jeton d'accès utilisateur standard et un jeton d'accès administrateur.  Par défaut, vous êtes dans le rôle d'utilisateur standard.  Pour exécuter le code nécessitant que vous soyez administrateur, vous devez d'abord élever vos privilèges d'utilisateur standard à administrateur.  Vous pouvez effectuer cela au démarrage d'une application en cliquant avec le bouton droit sur l'icône de l'application et en indiquant que vous voulez l'exécuter en tant qu'administrateur.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 L'exemple suivant montre comment déterminer l'identité du principal et les rôles disponibles pour celui\-ci.  Une application de cet exemple peut consister à confirmer que le rôle de l'utilisateur actuel l'autorise à utiliser votre application.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## Autorisation  
 L'autorisation est le processus qui consiste à déterminer si un principal est autorisé à exécuter l'opération demandée.  L'autorisation a lieu après l'authentification, et utilise les informations se rapportant à l'identité et aux rôles du principal pour déterminer les ressources auxquelles il peut avoir accès.  Vous pouvez utiliser la sécurité basée sur les rôles de .NET Framework pour l'implémentation de l'autorisation.  
  
## Problèmes de sécurité pour les mots clés virtuels internes  
 Il ne faut jamais baser la sécurité de votre application sur un membre marqué avec le modificateur [internal](../Topic/internal%20\(C%23%20Reference\).md) [virtual](../Topic/virtual%20\(C%23%20Reference\).md) en C\# \(modificateur [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md) [Friend](../Topic/Friend%20\(Visual%20Basic\).md) en Visual Basic\).  Bien que les membres marqués avec ces modificateurs ne puissent être remplacés que par d'autres membres dans l'assembly actuel, cette règle est uniquement appliquée par les langages C\# et Visual Basic.  Le runtime n'applique pas cette règle.  Il est donc possible de remplacer des membres marqués comme **internal virtual** en C\# et **Overloads Overridable Friend** en Visual Basic à l'aide du Microsoft Intermediate Language ou de n'importe quel autre langage qui n'applique pas cette règle.  
  
## Voir aussi  
 [Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md)