---
title: "Comment : anticiper des conditions d'espace insuffisant avec le stockage isolé"
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
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d813522d0aeb9bf37582c167760d44268df27039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="15300-102">Comment : anticiper des conditions d'espace insuffisant avec le stockage isolé</span><span class="sxs-lookup"><span data-stu-id="15300-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>
<span data-ttu-id="15300-103">Le code qui utilise le stockage isolé est limité par un [quota](../../../docs/standard/io/isolated-storage.md#quotas) qui spécifie la taille maximale du compartiment de données dans laquelle isolé des fichiers de stockage et de répertoires existent.</span><span class="sxs-lookup"><span data-stu-id="15300-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="15300-104">Le quota est défini par la stratégie de sécurité et peut être configuré par les administrateurs.</span><span class="sxs-lookup"><span data-stu-id="15300-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="15300-105">Si la valeur maximale autorisée de taille est dépassée lors de la tentative d’écriture de données, un <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception est levée et l’opération échoue.</span><span class="sxs-lookup"><span data-stu-id="15300-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="15300-106">Cela permet d’éviter les attaques par déni de service qui peut entraîner l’application à refuser des demandes, car le stockage des données est rempli.</span><span class="sxs-lookup"><span data-stu-id="15300-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>  
  
 <span data-ttu-id="15300-107">Pour vous aider à déterminer si une tentative d’écriture donnée peut échouer pour cette raison, le <xref:System.IO.IsolatedStorage.IsolatedStorage> classe fournit les trois propriétés en lecture seule : <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, et <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="15300-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="15300-108">Vous pouvez utiliser ces propriétés pour déterminer si l’écriture dans le magasin peut entraîner la taille maximale autorisée de la banque de dépassement.</span><span class="sxs-lookup"><span data-stu-id="15300-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="15300-109">N’oubliez pas que le stockage isolé est accessible simultanément ; Par conséquent, lorsque vous calculez la quantité de stockage restant, l’espace de stockage pouvant être consommé par le temps que vous tentez d’écrire dans le magasin.</span><span class="sxs-lookup"><span data-stu-id="15300-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="15300-110">Toutefois, vous pouvez utiliser la taille maximale de la banque pour aider à déterminer si la limite maximale de stockage disponible est sur le point d’être atteint.</span><span class="sxs-lookup"><span data-stu-id="15300-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>  
  
 <span data-ttu-id="15300-111">Le <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> propriété dépend de la preuve de l’assembly fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="15300-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="15300-112">Pour cette raison, vous devez récupérer cette propriété uniquement sur <xref:System.IO.IsolatedStorage.IsolatedStorageFile> les objets qui ont été créés à l’aide de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="15300-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="15300-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>les objets qui ont été créés dans une autre façon (par exemple, les objets retournés à partir de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> (méthode)) ne retourne pas une taille maximale.</span><span class="sxs-lookup"><span data-stu-id="15300-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15300-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="15300-114">Example</span></span>  
 <span data-ttu-id="15300-115">L’exemple de code suivant obtient un magasin isolé, crée des fichiers et récupère la <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="15300-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="15300-116">L’espace restant est indiqué en octets.</span><span class="sxs-lookup"><span data-stu-id="15300-116">The remaining space is reported in bytes.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="15300-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15300-117">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="15300-118">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="15300-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="15300-119">Obtention de magasins</span><span class="sxs-lookup"><span data-stu-id="15300-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
