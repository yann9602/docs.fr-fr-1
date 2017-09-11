---
title: "Guide pratique pour créer un fichier ou un dossier (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 150190eeef829bd0431eeea7789025b9905553e3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="b7cfa-102">Guide pratique pour créer un fichier ou un dossier (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b7cfa-102">How to: Create a File or Folder (C# Programming Guide)</span></span>
<span data-ttu-id="b7cfa-103">Vous pouvez par programmation créer un dossier sur votre ordinateur, créer un sous-dossier, créer un fichier dans le sous-dossier et écrire des données dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7cfa-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7cfa-104">Example</span></span>  
 <span data-ttu-id="b7cfa-105">[!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b7cfa-105">[!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]</span></span>  
  
 <span data-ttu-id="b7cfa-106">Si le dossier existe déjà, <xref:System.IO.Directory.CreateDirectory%2A> est sans effet et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-106">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="b7cfa-107">Toutefois, <xref:System.IO.File.Create%2A?displayProperty=fullName> remplace un fichier existant par un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-107">However, <xref:System.IO.File.Create%2A?displayProperty=fullName> replaces an existing file with a new file.</span></span> <span data-ttu-id="b7cfa-108">L’exemple utilise une instruction `if`-`else` pour éviter qu’un fichier existant soit pas remplacé.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-108">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="b7cfa-109">En apportant les modifications suivantes dans l’exemple, vous pouvez spécifier des résultats différents si un fichier avec un nom spécifique existe déjà.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-109">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="b7cfa-110">Si un tel fichier n’existe pas, le code en crée un.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-110">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="b7cfa-111">Si un tel fichier existe, le code ajoute des données à ce fichier.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-111">If such a file exists, the code appends data to that file.</span></span>  
  
-   <span data-ttu-id="b7cfa-112">Spécifiez un nom de fichier non aléatoire.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-112">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   <span data-ttu-id="b7cfa-113">Remplacez l’instruction `if`-`else` par l’instruction `using` dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-113">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="b7cfa-114">Exécutez l’exemple plusieurs fois pour vérifier que les données sont ajoutées au fichier à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-114">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="b7cfa-115">Pour découvrir d’autres valeurs `FileMode` que vous pouvez essayer, consultez <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-115">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="b7cfa-116">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b7cfa-117">Le nom du dossier est mal formé.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-117">The folder name is malformed.</span></span> <span data-ttu-id="b7cfa-118">Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (classe <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b7cfa-118">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="b7cfa-119">Utilisez la classe <xref:System.IO.Path> pour créer des noms de chemin valides.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-119">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
-   <span data-ttu-id="b7cfa-120">Le dossier parent du dossier à créer est en lecture seule (classe <xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b7cfa-120">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="b7cfa-121">Le nom du dossier est `null` (classe <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b7cfa-121">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="b7cfa-122">Le nom du dossier est trop long (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b7cfa-122">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="b7cfa-123">Le nom du dossier est uniquement un signe deux-points, « : » (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b7cfa-123">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b7cfa-124">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b7cfa-124">.NET Framework Security</span></span>  
 <span data-ttu-id="b7cfa-125">Une instance de la classe <xref:System.Security.SecurityException> peut être levée dans les situations de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-125">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="b7cfa-126">Si vous n’êtes pas autorisé à créer le dossier, l’exemple lève une instance de la classe <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="b7cfa-126">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7cfa-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7cfa-127">See Also</span></span>  
 <span data-ttu-id="b7cfa-128"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b7cfa-128"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="b7cfa-129">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b7cfa-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="b7cfa-130">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b7cfa-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)

