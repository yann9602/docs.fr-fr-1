---
title: "Guide pratique pour créer un fichier en Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- text files, creating
- files, creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: d06d274b31afad0a437405d1679e0be7548f2e14
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="bbfb4-102">Guide pratique pour créer un fichier en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bbfb4-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="bbfb4-103">Cet exemple crée un fichier texte vide à l’emplacement spécifié à l’aide de la méthode <xref:System.IO.File.Create%2A> de la classe <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbfb4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="bbfb4-104">Example</span></span>  
 <span data-ttu-id="bbfb4-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bbfb4-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bbfb4-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bbfb4-106">Compiling the Code</span></span>  
 <span data-ttu-id="bbfb4-107">Utilisez la variable `file` pour écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-107">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bbfb4-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="bbfb4-108">Robust Programming</span></span>  
 <span data-ttu-id="bbfb4-109">Si le fichier existe déjà, il est remplacé.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-109">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="bbfb4-110">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="bbfb4-111">Le chemin d'accès est mal formé.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-111">The path name is malformed.</span></span> <span data-ttu-id="bbfb4-112">Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bbfb4-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="bbfb4-113">Le chemin est en lecture seule (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="bbfb4-113">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="bbfb4-114">Le nom du chemin est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="bbfb4-114">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="bbfb4-115">Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="bbfb4-115">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="bbfb4-116">Le chemin n’est pas valide (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="bbfb4-116">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="bbfb4-117">Le chemin n’est constitué que d’un signe deux-points « : » (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="bbfb4-117">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bbfb4-118">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bbfb4-118">.NET Framework Security</span></span>  
 <span data-ttu-id="bbfb4-119">Une <xref:System.Security.SecurityException> peut être levée dans les environnements de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-119">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="bbfb4-120">L’appel à la méthode <xref:System.IO.File.Create%2A> nécessite <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-120">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="bbfb4-121">Une <xref:System.UnauthorizedAccessException> est levée si l’utilisateur n’est pas autorisé à créer le fichier.</span><span class="sxs-lookup"><span data-stu-id="bbfb4-121">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfb4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbfb4-122">See Also</span></span>  
 <span data-ttu-id="bbfb4-123"><xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="bbfb4-123"><xref:System.IO></span></span>   
 <span data-ttu-id="bbfb4-124"><xref:System.IO.File.Create%2A></span><span class="sxs-lookup"><span data-stu-id="bbfb4-124"><xref:System.IO.File.Create%2A></span></span>   
 <span data-ttu-id="bbfb4-125">[Utilisation de bibliothèques à partir de code d’un niveau de confiance partiel](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span><span class="sxs-lookup"><span data-stu-id="bbfb4-125">[Using Libraries from Partially Trusted Code](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span></span>  
 [<span data-ttu-id="bbfb4-126">Notions fondamentales de la sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="bbfb4-126">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

