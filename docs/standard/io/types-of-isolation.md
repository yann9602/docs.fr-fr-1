---
title: Types d'isolation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6b07c090a381925f5330a820214126a121d3790b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-isolation"></a>Types d'isolation
Accès au stockage isolé est toujours limité à l’utilisateur qui l’a créée. Pour implémenter ce type d’isolation, le common language runtime utilise la même notion d’identité de l’utilisateur que le système d’exploitation reconnaît, qui est l’identité associée au processus dans lequel le code s’exécute lorsque le magasin est ouvert. Cette identité est une identité de l’utilisateur authentifié, mais l’emprunt d’identité peut provoquer l’identité de l’utilisateur actuel pour modifier dynamiquement.  
  
 Accès au stockage isolé est également limité en fonction de l’identité associée avec le domaine et d’assembly de l’application ou à l’assembly uniquement. Le runtime obtient ces identités des façons suivantes :  
  
-   Identité de domaine représente la preuve de l’application, dans le cas d’une application web peut être l’URL complète. Pour le code hébergé par l’interpréteur de commandes, l’identité de domaine peut être basée sur le chemin de répertoire d’application. Par exemple, si l’exécutable s’exécute à partir du chemin d’accès C:\Office\MyApp.exe, l’identité de domaine serait C:\Office\MyApp.exe.  
  
-   Identité d’assembly est la preuve de l’assembly. Cela peut provenir d’une signature numérique de chiffrement, qui peut être l’assembly [nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md), l’éditeur de logiciel de l’assembly ou son identité URL. Si un assembly porte un nom fort et une identité d’éditeur de logiciel, l’identité de serveur de publication de logiciels est utilisée. Si l’assembly provenance d’Internet et n’est pas signé, l’identité de l’URL est utilisée. Pour plus d’informations sur les assemblys et les noms forts, consultez [programmation avec des assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md).  
  
-   Magasins itinérants se déplacent avec un utilisateur qui dispose d’un profil utilisateur itinérant. Les fichiers sont écrits dans un répertoire réseau et sont téléchargés à n’importe quel ordinateur, l’utilisateur se connecte. Pour plus d’informations sur les profils utilisateur itinérants, consultez <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 En combinant les concepts de l’utilisateur, le domaine et identité de l’assembly, le stockage isolé peut isoler des données de plusieurs manières, chacune ayant ses propres scénarios d’utilisation :  
  
-   [Isolation par utilisateur et par assembly](#UserAssembly)  
  
-   [Isolation par utilisateur, domaine et par assembly](#UserDomainAssembly)  
  
 Chacune de ces isolations peuvent être combinées avec un profil utilisateur itinérant. Pour plus d’informations, consultez la section [le stockage isolé et profil itinérant](#Roaming).  
  
 L’illustration suivante montre comment les magasins sont isolés dans différentes portées.  
  
 ![Isolation par utilisateur et par assembly](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
Types de stockage isolé  
  
 Notez que, à l’exception des magasins itinérants, le stockage isolé est toujours implicitement isolé par l’ordinateur, car il utilise les installations de stockage qui sont locales sur un ordinateur donné.  
  
> [!IMPORTANT]
>  Le stockage isolé n'est pas disponible pour les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. À la place, utilisez les classes de données d'application des espaces de noms `Windows.Storage` inclus dans l'API [!INCLUDE[wrt](../../../includes/wrt-md.md)] pour stocker des données locales et des fichiers. Pour plus d’informations, consultez [Données d’applications](http://go.microsoft.com/fwlink/?LinkId=229175) dans le Centre de développement Windows.  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>Isolation par utilisateur et par assembly  
 Lorsque l’assembly qui utilise les données de magasin doit être accessible à partir de n’importe quel domaine d’application, l’isolation par utilisateur et par assembly est appropriée. En règle générale, dans ce cas, le stockage isolé est utilisé pour stocker les données qui s’applique à plusieurs applications et ne sont pas liées à une application spécifique, tel que le nom d’utilisateur ou des informations de licence. Pour accéder au stockage isolé par utilisateur et par assembly, le code doit être approuvé pour transférer des informations entre les applications. En règle générale, l’isolation par utilisateur et par assembly est autorisée sur les intranets mais pas sur Internet. Appel de la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> (méthode) et le passage d’un utilisateur et un assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> retourne le stockage avec ce type d’isolation.  
  
 L’exemple de code suivant extrait un magasin isolé par utilisateur et par assembly. Le magasin est accessible via la `isoFile` objet.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Pour obtenir un exemple qui utilise les paramètres de la preuve, consultez <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 Le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> méthode est disponible comme un raccourci, comme illustré dans l’exemple de code suivant. Ce raccourci ne peut pas être utilisé pour ouvrir des magasins capables d’itinérance ; utiliser <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> dans ce cas.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>Isolation par utilisateur, par domaine et par assembly  
 Si votre application utilise un assembly tiers qui nécessite une banque de données privées, vous pouvez utiliser le stockage isolé pour stocker les données privées. Isolation par utilisateur, domaine et par assembly garantit que seul code d’un assembly donné peut accéder aux données et uniquement lorsque l’assembly est utilisé par l’application en cours d’exécution lorsque l’assembly créé le magasin et uniquement lors de l’exécution de l’utilisateur pour lequel le magasin a été créé le  application. Isolation par utilisateur, domaine et par assembly empêche l’assembly de tiers à partir de la fuite de données à d’autres applications. Ce type d’isolation doit être votre choix par défaut si vous savez que vous souhaitez utiliser le stockage isolé, mais ne savez pas vraiment le type d’isolation à utiliser. Appel de la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> méthode de <xref:System.IO.IsolatedStorage.IsolatedStorageFile> et en passant un utilisateur, domaine et par assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> retourne le stockage avec ce type d’isolation.  
  
 L’exemple de code suivant extrait un magasin isolé par utilisateur, domaine et par assembly. Le magasin est accessible via la `isoFile` objet.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Une autre méthode est disponible comme un raccourci, comme illustré dans l’exemple de code suivant. Ce raccourci ne peut pas être utilisé pour ouvrir des magasins capables d’itinérance ; utiliser <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> dans ce cas.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>Stockage et profil itinérant isolé  
 Les profils utilisateur itinérants sont une fonctionnalité de Windows qui permet à un utilisateur de configurer une identité sur un réseau et utiliser cette identité pour se connecter à n’importe quel ordinateur du réseau, exécution sur tous les paramètres personnalisés. Un assembly qui utilise le stockage isolé peut spécifier que le stockage isolé de l’utilisateur doit se déplacer avec le profil utilisateur itinérant. Itinérance utilisable conjointement avec l’isolation par utilisateur et par assembly ou avec l’isolation par utilisateur, domaine et par assembly. Si une portée itinérante n’est pas utilisée, magasins ne suivront pas même si un profil utilisateur itinérant est utilisé.  
  
 L’exemple de code suivant récupère un magasin itinérant isolé par utilisateur et par assembly. Le magasin est accessible via la `isoFile` objet.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Une étendue de domaine peut être ajoutée pour créer un magasin itinérant isolé par utilisateur, de domaine et d’application. L’exemple de code suivant illustre cela.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
