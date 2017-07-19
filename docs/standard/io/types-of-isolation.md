---
title: "Types d&#39;isolation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "stocker des données à l’aide du stockage isolé, accéder à un stockage isolé"
  - "stocker des données à l’aide du stockage isolé, types d’isolation"
  - "authentification (.NET Framework), stockage isolé"
  - "assemblys (.NET Framework), identité"
  - "stockage isolé, accéder"
  - "stockage de données à l’aide du stockage isolé, types d’isolation"
  - "stockage de données à l’aide du stockage isolé, accéder à un stockage isolé"
  - "identité de domaine"
  - "stockage isolé, types"
  - "authentification utilisateur, stockage isolé"
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# Types d&#39;isolation
L'accès au stockage isolé est toujours limité à l'utilisateur qui l'a créé.  Pour implémenter ce type d'isolation, le Common Language Runtime utilise la même notion d'identité d'utilisateur que celle reconnue par le système d'exploitation, c'est\-à\-dire l'identité associée au processus dans lequel le code s'exécute lors de l'ouverture du magasin.  Cette identité est une identité d'utilisateur authentifiée, mais l'emprunt d'identité peut entraîner une modification dynamique de l'identité de l'utilisateur en cours.  
  
 Outre l'isolation par utilisateur, l'accès au stockage isolé est limité selon l'identité associée au domaine et à l'assembly de l'application ou à l'assembly uniquement.  Le runtime obtient ces identités des façons suivantes :  
  
-   L'identité de domaine représente la preuve de l'application \(par exemple, l'URL complète dans le cas d'une application Web\).  Pour le code hébergé dans le shell, l'identité de domaine peut se baser sur le chemin d'accès au répertoire de l'application.  Par exemple, si le fichier exécutable s'exécute à partir du chemin d'accès C:\\Office\\MyApp.exe, l'identité de domaine est C:\\Office\\MyApp.exe.  
  
-   L'identité d'assembly est la preuve de l'assembly.  Elle peut provenir d'une signature numérique de chiffrement, qui peut être le [nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md) de l'assembly, l'éditeur de logiciel de l'assembly ou son identité URL.  Si un assembly possède à la fois un nom fort et une identité d'éditeur de logiciel, cette dernière est utilisée.  Si l'assembly provient d'Internet et est non signé, l'identité URL est utilisée.  Pour plus d'informations sur les assemblys et les noms forts, consultez [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Les magasins itinérants se déplacent avec les utilisateurs qui possèdent un profil utilisateur itinérant.  Les fichiers sont écrits dans un répertoire réseau et sont téléchargés vers un ordinateur auquel se connecte l'utilisateur.  Pour plus d'informations sur les profils utilisateur itinérants, consultez <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=fullName>.  
  
 En associant les concepts d'identité d'utilisateur, de domaine et d'assembly, le stockage isolé peut isoler des données en utilisant les façons suivantes, chacune possédant ses propres scénarios d'usage :  
  
-   [Isolation par utilisateur et par assembly](#UserAssembly)  
  
-   [Isolation par utilisateur, par domaine et par assembly](#UserDomainAssembly)  
  
 Chacune de ces isolations peut être associée à un profil utilisateur itinérant.  Pour plus d'informations, consultez la section [Stockage d'isolement et errer](#Roaming).  
  
 L'illustration suivante démontre comment les magasins sont isolés dans diverses portées.  
  
 ![Isolation par utilisateur et par assembly.](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Types de stockage isolé  
  
 Notez qu'à l'exception des magasins itinérants, le stockage isolé est toujours implicitement isolé par l'ordinateur, car il utilise les installations de stockage qui sont locales à un ordinateur donné.  
  
> [!IMPORTANT]
>  Le stockage isolé est pas disponible pour les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  À la place, utilisez les classes de données d'application dans les espaces de noms `Windows.Storage` inclus dans l'API [!INCLUDE[wrt](../../../includes/wrt-md.md)] pour stocker des données locales et des fichiers.  Pour plus d'informations, consultez [Données d'applications](http://go.microsoft.com/fwlink/?LinkId=229175) sur le centre de développement Windows.  
  
<a name="UserAssembly"></a>   
## Isolation par utilisateur et par assembly  
 Lorsque l'assembly qui utilise le magasin de données doit être accessible à partir d'un domaine d'application, l'isolation par utilisateur et par assembly est appropriée.  Généralement, dans ce cas, le stockage isolé est utilisé pour stocker des données qui s'appliquent à plusieurs applications et n'est pas limité à une application spécifique, telle que le nom ou les informations sur la licence de l'utilisateur.  Pour accéder au stockage isolé par utilisateur et par assembly, le code doit être de confiance pour transférer des informations entre des applications.  Généralement, l'isolation par utilisateur et par assembly est autorisée sur les intranets mais pas sur Internet.  L'appel de la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=fullName> et le passage d'un utilisateur et d'un assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> renvoient le stockage avec ce type d'isolation.  
  
 L'exemple de code suivant extrait un magasin itinérant qui est isolé par utilisateur et par assembly.  Le magasin est accessible via l'objet `isoFile` .  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Pour obtenir un exemple qui utilise des paramètres de preuve, consultez <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> est disponible sous forme de raccourci, comme illustré par l'exemple de code suivant.  Ce raccourci ne peut pas être utilisé pour ouvrir des magasins itinérants ; dans ce cas, vous devez utiliser <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## Isolation par utilisateur, par domaine et par assembly  
 Si votre application utilise un assembly tiers nécessitant un magasin de données privé, vous pouvez utiliser un stockage isolé pour stocker des données privées.  L'isolation par utilisateur, par domaine et par assembly garantit que seul le code d'un assembly donné peut accéder aux données dans les situations suivantes uniquement : lorsque l'assembly est utilisé par l'application qui s'exécutait au moment où l'assembly créait le magasin et lorsque l'utilisateur pour lequel le magasin a été créé exécute l'application.  L'isolation par utilisateur, par domaine et par assembly empêche l'assembly tiers de divulguer des données à d'autres applications.  Ce type d'isolation doit être votre sélection par défaut si vous savez que vous souhaitez utiliser le stockage isolé mais que vous ne pouvez pas déterminer avec certitude le type d'isolation à utiliser.  Lorsque vous appelez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile> et que vous passez un utilisateur, un domaine et un assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> renvoie le stockage avec ce type d'isolation.  
  
 L'exemple de code suivant extrait un magasin isolé par utilisateur, par domaine et par assembly.  Le magasin est accessible via l'objet `isoFile`.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Une autre méthode est disponible sous forme de raccourci, comme illustré par l'exemple de code suivant.  Ce raccourci ne peut pas être utilisé pour ouvrir des magasins qui sont itinérants ; dans ce cas, vous devez utiliser <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## Stockage et profil itinérant isolé  
 Les profils utilisateurs itinérants sont une fonctionnalité Windows qui permet aux utilisateurs de définir une identité sur un réseau et pour utiliser cette identité pour vous connecter à n'importe quel ordinateur sur le réseau, reportant tous les paramètres personnalisés.  Un assembly qui utilise le stockage isolé peut spécifier que le stockage isolé de l'utilisateur devrait se déplacer avec le profil d'utilisateur itinérant.  Le profil itinérant peut être utilisé conjointement avec l'isolation par utilisateur et par assembly ou avec l'isolation par utilisateur, par domaine et par assembly.  Si aucune portée itinérante n'est utilisée, les magasins ne seront pas itinérants même en cas d'utilisation d'un profil d'utilisateur itinérant.  
  
 L'exemple de code suivant extrait un magasin itinérant isolé par utilisateur et par assembly.  Le magasin est accessible via l'objet `isoFile` .  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Une portée de domaine peut être ajoutée afin de créer un magasin itinérant isolé par utilisateur, par domaine et par application.  L'exemple de code suivant illustre ceci.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)