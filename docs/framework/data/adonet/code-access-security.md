---
title: "S&#233;curit&#233; d&#39;acc&#232;s du code et ADO.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 93e099eb-daa1-4f1e-b031-c1e10a996f88
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# S&#233;curit&#233; d&#39;acc&#232;s du code et ADO.NET
Le .NET Framework offre une sécurité basée sur les rôles ainsi qu'une sécurité d'accès du code \(CAS, Code Access Security\) implémentées à l'aide d'une infrastructure commune fournie par le Common Language Runtime \(CLR\).  Dans l'univers du code non managé, la plupart des applications s'exécutent avec les autorisations de l'utilisateur ou d'une principal de sécurité.  C'est pourquoi les systèmes informatiques peuvent être endommagés et des données privées compromises lorsqu'un utilisateur bénéficiant de privilèges élevés exécute des logiciels malveillants ou remplis d'erreurs.  
  
 En revanche, le code managé exécuté dans le .NET Framework inclut une sécurité d'accès du code qui s'applique au code seul.  L'autorisation ou l'interdiction pour le code de s'exécuter dépend de son origine et d'autres aspects de son identité, et pas seulement de l'identité de la principal de sécurité.  Cela réduit la probabilité que du code managé puisse être utilisé de façon abusive.  
  
## Autorisations d'accès du code  
 Lors de l'exécution du code, ce dernier présente une preuve qui est évaluée par le système de sécurité CLR.  Généralement, cette preuve comprend l'origine du code, notamment l'URL, le site, la zone et les signatures numériques qui garantissent l'identité de l'assembly.  
  
 Le CLR permet au code d'effectuer uniquement les opérations pour lesquelles il dispose d'une autorisation.  Le code peut demander des autorisations qui lui sont accordées en fonction de la stratégie de sécurité définie par un administrateur.  
  
> [!NOTE]
>  Le code s'exécutant dans le CLR ne peut pas s'octroyer d'autorisations à lui\-même.  Par exemple, un code peut demander et obtenir moins d'autorisations qu'une stratégie de sécurité le prévoit, mais il ne pourra jamais en obtenir plus.  Lors de l'octroi d'autorisations, démarrez sans autorisation, puis ajoutez les autorisations les plus restrictives pour la tâche en cours d'exécution.  Démarrer avec toutes les autorisations puis en refuser individuellement génère des applications non sécurisées susceptibles de contenir des failles de sécurité involontaires dues à l'octroi de davantage d'autorisations que nécessaire.  Pour plus d’informations, consultez [NIB: Configuring Security Policy](http://msdn.microsoft.com/fr-fr/0f130bcd-1bba-4346-b231-0bcca7dab1a4) et [NIB: Security Policy Management](http://msdn.microsoft.com/fr-fr/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
 Il existe trois types d'autorisations d'accès du code :  
  
-   Les `Code access permissions` sont dérivées de la classe <xref:System.Security.CodeAccessPermission>.  Des autorisations sont requises pour accéder à des ressources protégées, telles que des fichiers et des variables d'environnement, ainsi que pour effectuer des opérations protégées, telles que l'accès à du code non managé.  
  
-   Les `Identity permissions` représentent les caractéristiques qui identifient un assembly.  Des autorisations sont octroyées à un assembly sur la base d'une preuve, qui peut consister en différents éléments, tels qu'une signature numérique ou la provenance du code.  Les autorisations d'identité dérivent également de la classe de base <xref:System.Security.CodeAccessPermission>.  
  
-   Les `Role-based security permissions` sont basées sur le fait qu'une principal de sécurité possède une identité spécifiée ou soit membre d'un rôle particulier.  La classe <xref:System.Security.Permissions.PrincipalPermission> permet de procéder à des vérifications d'autorisations déclaratives et impératives par rapport à la principal de sécurité active.  
  
 Pour déterminer si le code est autorisé à accéder à une ressources ou effectuer une opération, le système de sécurité du runtime parcourt la pile des appels, en comparant les autorisations de chaque appelant à l'autorisation faisant l'objet d'une demande.  Si un appelant dans la pile des appels ne possède pas l'autorisation demandée, une exception <xref:System.Security.SecurityException> est levée et l'accès est refusé.  
  
### Demande d'autorisations  
 Les demandes d'autorisations ont pour but d'indiquer au runtime les autorisations dont votre application a besoin pour s'exécuter et de garantir que seules les autorisations requises lui sont octroyées.  Par exemple, si votre application doit écrire des données sur le disque local, elle nécessite <xref:System.Security.Permissions.FileIOPermission>.  Si cette autorisation n'a pas été accordée, l'application échoue lorsqu'elle tente d'écrire sur le disque.  Cependant, si l'application demande `FileIOPermission` et que cette autorisation lui a été refusée, l'application génère l'exception dès le départ et ne se charge pas.  
  
 Dans un scénario dans lequel l'application a seulement besoin de lire des données du disque, vous pouvez demander à ce qu'aucune autorisation d'accès en écriture ne lui soit jamais octroyée.  En cas de bogue ou d'attaque malveillante, votre code ne peut pas altérer les données sur lesquelles il opère.  Pour plus d'informations, consultez [NIB: Requesting Permissions](http://msdn.microsoft.com/fr-fr/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
## Sécurité basée sur les rôles et sécurité d'accès du code \(CAS\)  
 L'implémentation de la sécurité basée sur les rôles et de la sécurité d'accès du code \(CAS\) améliore la sécurité globale de votre application.  La sécurité basée sur les rôles peut utiliser un compte Windows ou une identité personnalisée, en mettant à la disposition du thread actuel des informations sur la principal de sécurité.  Par ailleurs, les applications doivent souvent accorder l'accès aux données et aux ressources en fonction des informations d'identification fournies par l'utilisateur.  Généralement, ces applications vérifient le rôle de l'utilisateur afin de lui donner accès aux ressources correspondant à ce rôle.  
  
 La sécurité basée sur les rôles permet à un composant d'identifier les utilisateurs actuels et leurs rôles associés au moment de l'exécution.  Ces informations sont ensuite mappées à l'aide d'une stratégie de sécurité d'accès du code pour déterminer le jeu d'autorisations octroyées au moment de l'exécution.  Pour un domaine d'application spécifié, l'hôte peut modifier la stratégie de sécurité basée sur les rôles par défaut et définir une principal de sécurité par défaut qui représente un utilisateur et les rôles qui lui sont associés.  
  
 Le CLR utilise des autorisations pour mettre en œuvre son mécanisme destiné à imposer des restrictions sur du code managé.  Les autorisations de sécurité basées sur les rôles fournissent un mécanisme permettant de savoir si un utilisateur \(ou l'agent qui agit en son nom\) possède une identité particulière ou est membre d'un rôle spécifié.  Pour plus d'informations, consultez [Security Permissions](http://msdn.microsoft.com/fr-fr/b03757b4-e926-4196-b738-3733ced2bda0).  
  
 En fonction du type d'application en cours de construction, vous devez également envisager d'implémenter des autorisations basées sur les rôles dans la base de données.  Pour plus d'informations sur la sécurité basée sur les rôles dans SQL Server, voir [Sécurité de SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-security.md).  
  
## Assemblys  
 Les assemblys constituent l'unité fondamentale dans le déploiement, le contrôle de version, la portée d'activation et les autorisations de sécurité d'une application .NET Framework.  Ils fournissent une collection de types et de ressources qui sont générés pour fonctionner ensemble et former une unité logique de fonctionnalités.  Pour le CLR, un type n'existe pas en dehors du contexte d'un assembly.  Pour plus d'informations sur la création et le déploiement des assemblys, voir [Programmation à l'aide d'assemblys](../../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
### Attribution d'un nom fort à des assemblys  
 Un nom fort, ou signature numérique, est constitué de l'identité de l'assembly \(son simple nom textuel, son numéro de version et des informations de culture, le cas échéant\) ainsi que d'une clé publique et d'une signature numérique.  La signature numérique est générée à partir un fichier d'assembly à l'aide de la clé privée correspondante.  Le fichier d'assembly contient le manifeste d'assembly, qui à son tour comporte les noms et les hachages de tous les fichiers qui composent l'assembly.  
  
 L'attribution d'un nom fort à un assembly donne à une application ou un composant une identité unique que d'autres logiciels peuvent utiliser pour s'y référer explicitement.  L'attribution de noms forts aux assemblys les protège contre des falsifications par un assembly contenant un code hostile.  Elle garantit également la cohérence du contrôle des versions d'un composant.  Vous devez attribuer un nom fort aux assemblys qui seront déployés sur le cache GAC \(Global Assembly Cache\).  Pour plus d'informations, consultez [Création et utilisation d'assemblys avec nom fort](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## Confiance partielle dans ADO.NET 2.0  
 Dans ADO.NET 2.0, le fournisseur de données .NET Framework pour SQL Server , le fournisseur de données .NET Framework pour OLE DB, le fournisseur de données .NET Framework pour ODBC et le fournisseur de données .NET Framework pour Oracle peuvent tous s'exécuter dans des environnements bénéficiant d'une confiance partielle.  Dans les versions précédentes du .NET Framework, seul <xref:System.Data.SqlClient> était pris en charge dans des applications ne bénéficiant pas d'une confiance totale.  
  
 Au minimum, une application avec confiance partielle utilisant le fournisseur SQL Server doit disposer d'autorisations d'exécution et de l'objet <xref:System.Data.SqlClient.SqlClientPermission>.  
  
### Propriétés d'attribut d'autorisation pour la confiance partielle  
 Pour des scénarios de confiance partielle, vous pouvez utiliser des membres de l'objet <xref:System.Data.SqlClient.SqlClientPermissionAttribute> pour restreindre davantage les capacités disponibles pour le fournisseur de données .NET Framework pour SQL Server.  
  
 Le tableau suivant répertorie les propriétés de l'objet <xref:System.Data.SqlClient.SqlClientPermissionAttribute> disponibles et leurs descriptions :  
  
|Propriété d'attribut d'autorisation|Description|  
|-----------------------------------------|-----------------|  
|`Action`|Obtient ou définit une action de sécurité.  Hérité de l'objet <xref:System.Security.Permissions.SecurityAttribute>.|  
|`AllowBlankPassword`|Active ou désactive l'utilisation d'un mot de passe vide dans une chaîne de connexion.  Les valeurs valides sont `true` \(pour activer l'utilisation des mots de passe vides\) et `false` \(pour la désactiver\).  Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`ConnectionString`|Identifie une chaîne de connexion autorisée.  Plusieurs chaînes de connexion peuvent être identifiées. **Note:**  N'incluez pas d'ID utilisateur ni de mot de passe dans votre chaîne de connexion.  Dans cette version, vous ne pouvez pas modifier les restrictions liées à la chaîne de connexion à l'aide de l'outil de configuration .NET Framework. <br /><br /> Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictions`|Identifie les paramètres de chaîne de connexion autorisés et non autorisés.  Les paramètres de chaîne de connexion suivent le format *\<nom de paramètre\>\=*.  Il est possible de spécifier plusieurs paramètres, délimités par un point\-virgule \(;\). **Note:**  Si aucun `KeyRestrictions` n'est spécifié et que la propriété `KeyRestrictionBehavior` a la valeur `AllowOnly` ou `PreventUsage`, aucun paramètre de chaîne de connexion supplémentaire n'est autorisé.  Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`KeyRestrictionBehavior`|Identifie les paramètres de chaîne de connexion comme étant les seuls paramètres supplémentaires autorisés \(`AllowOnly`\) ou identifie les paramètres supplémentaires qui ne sont pas autorisés \(`PreventUsage`\).  `AllowOnly` est la valeur par défaut.  Hérité de l'objet <xref:System.Data.Common.DBDataPermissionAttribute>.|  
|`TypeID`|Obtient un identificateur unique pour cet attribut lors de l'implémentation dans une classe dérivée.  Hérité de l'objet <xref:System.Attribute>.|  
|`Unrestricted`|Indique si une autorisation illimitée à la ressource est déclarée.  Hérité de l'objet <xref:System.Security.Permissions.SecurityAttribute>.|  
  
#### Syntaxe de ConnectionString  
 L'exemple suivant illustre l'utilisation de l'élément `connectionStrings` d'un fichier de configuration pour n'autoriser l'utilisation que d'une seule chaîne de connexion spécifique.  Voir [Chaînes de connexion](../../../../docs/framework/data/adonet/connection-strings.md) pour plus d'informations sur le stockage et l'extraction de chaînes de connexion à partir de fichiers de configuration.  
  
```  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;" />  
</connectionStrings>  
```  
  
#### Syntaxe de KeyRestrictions  
 L'exemple suivant active la même chaîne de connexion, active l'utilisation des options de chaîne de connexion `Encrypt` et `Packet``Size` mais restreint l'utilisation de toute autre option de chaîne de connexion.  
  
```  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Encrypt=;Packet Size=;"  
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
#### KeyRestrictionBehavior avec la syntaxe de PreventUsage  
 L'exemple suivant active la même chaîne de connexion et autorise tous les autres paramètres de connexion à l'exception de `User Id`, `Password` et `Persist Security Info`.  
  
```  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="User Id=;Password=;Persist Security Info=;"  
    KeyRestrictionBehavior="PreventUsage" />  
</connectionStrings>  
```  
  
#### KeyRestrictionBehavior avec la syntaxe de AllowOnly  
 L'exemple suivant active deux chaînes de connexion qui contiennent également des paramètres `Initial Catalog`, `Connection Timeout`, `Encrypt` et `Packet Size`.  L'utilisation de tous les autres paramètres de chaîne de connexion est restreinte.  
  
```  
<connectionStrings>  
  <add name="DatabaseConnection"   
    connectionString="Data Source=(local);Initial   
    Catalog=Northwind;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
  
  <add name="DatabaseConnection2"   
    connectionString="Data Source=SqlServer2;Initial   
    Catalog=Northwind2;Integrated Security=true;"  
    KeyRestrictions="Initial Catalog;Connection Timeout=;  
       Encrypt=;Packet Size=;"   
    KeyRestrictionBehavior="AllowOnly" />  
</connectionStrings>  
```  
  
### Activation de confiance partielle avec un jeu d'autorisations personnalisé  
 Pour activer l'utilisation d'autorisations <xref:System.Data.SqlClient> pour une zone particulière, un administrateur système doit créer un jeu d'autorisations personnalisé et le définir comme jeu d'autorisations pour une zone particulière.  Les jeux d'autorisations par défaut, tels que `LocalIntranet`, ne peuvent pas être modifiés.  Par exemple, pour inclure des autorisations <xref:System.Data.SqlClient> pour du code dans lequel l'objet <xref:System.Security.Policy.Zone> a une valeur `LocalIntranet`, un administrateur système peut copier le jeu d'autorisations pour `LocalIntranet`, le renommer en « CustomLocalIntranet », ajouter les autorisations <xref:System.Data.SqlClient>, importer le jeu d'autorisations CustomLocalIntranet à l'aide du [Caspol.exe \(Code Access Security Policy Tool\)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md), puis définir CustomLocalIntranet comme jeu d'autorisations de `LocalIntranet_Zone`.  
  
### Exemple de jeu d'autorisations  
 Voici un exemple de jeu d'autorisations destiné au fournisseur de données .NET Framework pour SQL Serveur dans un scénario à confiance partielle.  Pour plus d'informations sur la création de jeux d'autorisations, voir [NIB:Configuring Permission Sets Using Caspol.exe](http://msdn.microsoft.com/fr-fr/94e2625e-21ad-4038-af36-6d1f9df40a57).  
  
```  
<PermissionSet class="System.Security.NamedPermissionSet"  
  version="1"  
  Name="CustomLocalIntranet"  
  Description="Custom permission set given to applications on  
    the local intranet">  
  
<IPermission class="System.Data.SqlClient.SqlClientPermission, System.Data, Version=2.0.0000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
version="1"  
AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Integrated Security=true;"  
 KeyRestrictions="Initial Catalog=;Connection Timeout=;  
   Encrypt=;Packet Size=;"   
 KeyRestrictionBehavior="AllowOnly" />  
 </IPermission>  
</PermissionSet>  
```  
  
## Vérification de l'accès du code ADO.NET à l'aide des autorisations de sécurité  
 Dans les scénarios avec confiance partielle, vous pouvez exiger des privilèges de sécurité d'accès du code \(CAS\) pour des méthodes particulières dans votre code en spécifiant un objet <xref:System.Data.SqlClient.SqlClientPermissionAttribute>.  Si ce privilège n'est pas autorisé par la stratégie de sécurité limitée en vigueur, une exception est levée avant que votre code soit exécuté.  Pour plus d'informations sur les stratégies de sécurité, voir [NIB: Security Policy Management](http://msdn.microsoft.com/fr-fr/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9) et [NIB: Security Policy Best Practices](http://msdn.microsoft.com/fr-fr/d49bc4d5-efb7-4caa-a2fe-e4d3cec63c05).  
  
### Exemple  
 L'exemple suivant montre comment écrire un code requérant une chaîne de connexion particulière.  Il simule le refus d'autorisations illimitées à <xref:System.Data.SqlClient>, qu'un administrateur système implémenterait à l'aide d'une stratégie de sécurité d'accès du code dans la réalité.  
  
> [!IMPORTANT]
>  En cas d'utilisation d'autorisations de sécurité d'accès du code pour ADO.NET, le modèle correct consiste à commencer par le cas le plus restrictif \(aucune autorisation\) puis à ajouter les autorisations spécifiques nécessaires pour la tâche particulière que le code doit exécuter.  En revanche, commencer par toutes les autorisations, puis tenter de refuser une autorisation spécifique n'est pas une approche sûre car il existe de nombreuses manières d'exprimer la même chaîne de connexion.  Par exemple, si vous démarrez avec toutes les autorisations, puis refusez l'utilisation de la chaîne de connexion "server\=someserver", vous pouvez continuer à utiliser "server\=someserver.mycompany.com".  En démarrant toujours en n'accordant aucune autorisation, vous limitez les risques de failles dans le jeu d'autorisations.  
  
 Le code suivant montre comment `SqlClient` exécute la demande de sécurité qui lève un objet <xref:System.Security.SecurityException> si les autorisations de sécurité d'accès du code \(CAS\) appropriées ne sont pas en place.  Le résultat de l'objet <xref:System.Security.SecurityException> s'affiche dans la fenêtre de console.  
  
 [!code-csharp[DataWorks SqlClient.CAS#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.CAS#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.CAS/VB/source.vb#1)]  
  
 Vous devez voir ce résultat dans la fenêtre Console :  
  
```  
Failed, as expected: <IPermission class="System.Data.SqlClient.  
SqlClientPermission, System.Data, Version=2.0.0.0,   
  Culture=neutral, PublicKeyToken=b77a5c561934e089" version="1"  
  AllowBlankPassword="False">  
<add ConnectionString="Data Source=(local);Initial Catalog=  
  Northwind;Integrated Security=SSPI" KeyRestrictions=""  
KeyRestrictionBehavior="AllowOnly"/>  
</IPermission>  
  
Connection opened, as expected.  
Failed, as expected: Request failed.  
```  
  
## Interopérabilité avec du code non managé  
 Le code qui s'exécute en dehors du CLR est appelé code non managé.  Par conséquent, les mécanismes de sécurité, tels que la sécurité d'accès du code, ne peuvent pas être appliqués à du code non managé.  Les composants COM, les interfaces ActiveX et les fonctions API Win32 sont des exemples de code non managé.  Des considérations de sécurité particulières s'appliquent lors de l'exécution de code non managé pour éviter de compromettre la sécurité globale des applications.  Pour plus d'informations, consultez [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).  
  
 Le .NET Framework prend également en charge la compatibilité descendante avec des composants COM existants en offrant un accès via COM Interop.  Vous pouvez incorporer des composants COM dans une application .NET Framework en utilisant des outils de COM Interop pour importer les types COM pertinents.  Une fois importés, les types COM sont prêts à être utilisés.  COM Interop permet également aux clients COM d'accéder à du code managé en exportant des métadonnées d'assembly dans une bibliothèque de types et en inscrivant le composant managé en tant que composant COM.  Pour plus d'informations, consultez [Advanced COM Interoperability](http://msdn.microsoft.com/fr-fr/3ada36e5-2390-4d70-b490-6ad8de92f2fb).  
  
## Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [PAVE Security in Native and .NET Framework Code](http://msdn.microsoft.com/fr-fr/bd61be84-c143-409a-a75a-44253724f784)   
 [Code Access Security](http://msdn.microsoft.com/fr-fr/23a20143-241d-4fe5-9d9f-3933fd594c03)   
 [Role\-Based Security](http://msdn.microsoft.com/fr-fr/239442e3-5be4-4203-b7fd-793baffea803)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)