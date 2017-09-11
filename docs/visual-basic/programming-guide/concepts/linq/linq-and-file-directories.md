---
title: "LINQ et répertoires de fichiers (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b9e814c9e9f8519522f288657d6940b07a0b3094
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-file-directories-visual-basic"></a><span data-ttu-id="9f6bf-102">LINQ et répertoires de fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-102">LINQ and File Directories (Visual Basic)</span></span>
<span data-ttu-id="9f6bf-103">Plusieurs opérations de système de fichiers sont des requêtes et sont donc parfaitement à l’approche LINQ.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-103">Many file system operations are essentially queries and are therefore well-suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="9f6bf-104">Notez que les requêtes de cette section sont non destructif.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-104">Note that the queries in this section are non-destructive.</span></span> <span data-ttu-id="9f6bf-105">Ils ne sont pas utilisés pour modifier le contenu des fichiers d’origine.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-105">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="9f6bf-106">Conformément à la règle que les requêtes ne devraient pas entraîner des effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-106">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="9f6bf-107">En règle générale, tout code (y compris les requêtes qui effectuent créent / mettre à jour / suppression des opérateurs) qui modifie les données sources doit rester distinct du code qui interroge uniquement les données.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-107">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="9f6bf-108">Cette section contient les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9f6bf-108">This section contains the following topics:</span></span>  
  
 [<span data-ttu-id="9f6bf-109">Comment : interroger des fichiers possédant un attribut spécifié ou un nom (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-109">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <span data-ttu-id="9f6bf-110">Montre comment rechercher des fichiers en examinant une ou plusieurs propriétés de son <xref:System.IO.FileInfo>objet.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="9f6bf-110">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 [<span data-ttu-id="9f6bf-111">Comment : regrouper des fichiers par Extension (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-111">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 <span data-ttu-id="9f6bf-112">Montre comment retourner des groupes de <xref:System.IO.FileInfo>objet selon leur extension de nom de fichier.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="9f6bf-112">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 [<span data-ttu-id="9f6bf-113">Comment : rechercher le nombre Total d’octets dans un ensemble de dossiers (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-113">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 <span data-ttu-id="9f6bf-114">Montre comment retourner le nombre total d’octets dans tous les fichiers dans une arborescence de répertoires spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-114">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="9f6bf-115">[Comment : comparer le contenu de deux dossiers (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span><span class="sxs-lookup"><span data-stu-id="9f6bf-115">[How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="9f6bf-116">Montre comment retourner tous les fichiers qui sont présents dans deux dossiers spécifiés et également tous les fichiers qui sont présents dans un dossier, mais pas l’autre.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-116">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 [<span data-ttu-id="9f6bf-117">Comment : interroger le plus grand nombre ou les fichiers dans une arborescence de répertoires (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-117">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 <span data-ttu-id="9f6bf-118">Montre comment retourner le fichier plus grand ou plus petit, ou un nombre spécifié de fichiers, dans une arborescence de répertoires.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-118">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 [<span data-ttu-id="9f6bf-119">Comment : interroger des fichiers dupliqués dans une arborescence de répertoires (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-119">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="9f6bf-120">Montre comment regrouper tous les noms de fichier qui se produisent dans plusieurs emplacements dans une arborescence de répertoires spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-120">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="9f6bf-121">Montre également comment effectuer des comparaisons plus complexes selon un comparateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-121">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 [<span data-ttu-id="9f6bf-122">Comment : interroger le contenu de fichiers dans un dossier (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-122">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 <span data-ttu-id="9f6bf-123">Montre comment effectuer une itération dans les dossiers dans une arborescence, ouvrez chaque fichier et interroger le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-123">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="9f6bf-124">Commentaires</span><span class="sxs-lookup"><span data-stu-id="9f6bf-124">Comments</span></span>  
 <span data-ttu-id="9f6bf-125">Il est plus complexe impliquées dans la création d’une source de données qui représente le contenu du système de fichiers et gère correctement les exceptions correctement.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-125">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="9f6bf-126">Les exemples dans cette section créent une collection instantanée de <xref:System.IO.FileInfo>des objets qui représentent tous les fichiers d’un dossier racine spécifié et tous ses sous-dossiers.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="9f6bf-126">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="9f6bf-127">L’état réel de chaque <xref:System.IO.FileInfo>peuvent changer dans le temps entre le début et la fin de l’exécution d’une requête.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="9f6bf-127">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="9f6bf-128">Par exemple, vous pouvez créer une liste de <xref:System.IO.FileInfo>des objets à utiliser comme source de données.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="9f6bf-128">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="9f6bf-129">Si vous essayez d’accéder à la `Length` propriété dans une requête, le <xref:System.IO.FileInfo>objet tente d’accéder au système de fichiers pour mettre à jour la valeur de `Length`.</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="9f6bf-129">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="9f6bf-130">Si le fichier n’existe plus, vous obtiendrez un <xref:System.IO.FileNotFoundException>dans votre requête, même si vous n’interrogiez pas le système de fichiers directement.</xref:System.IO.FileNotFoundException></span><span class="sxs-lookup"><span data-stu-id="9f6bf-130">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="9f6bf-131">Certaines requêtes de cette section utilisent une méthode distincte qui utilise ces exceptions particulières dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="9f6bf-131">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="9f6bf-132">Une autre option consiste à conserver votre source de données mis à jour dynamiquement en utilisant le <xref:System.IO.FileSystemWatcher>.</xref:System.IO.FileSystemWatcher></span><span class="sxs-lookup"><span data-stu-id="9f6bf-132">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6bf-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f6bf-133">See Also</span></span>  
 [<span data-ttu-id="9f6bf-134">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f6bf-134">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
