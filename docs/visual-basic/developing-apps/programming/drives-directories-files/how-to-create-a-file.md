---
title: "Guide pratique pour créer un fichier en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1ce74601136c870097d6d558e1f3ff12ba1c212
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="bc964-102">Guide pratique pour créer un fichier en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc964-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="bc964-103">Cet exemple crée un fichier texte vide à l’emplacement spécifié à l’aide de la méthode <xref:System.IO.File.Create%2A> de la classe <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="bc964-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc964-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc964-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc964-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bc964-105">Compiling the Code</span></span>  
 <span data-ttu-id="bc964-106">Utilisez la variable `file` pour écrire dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="bc964-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bc964-107">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="bc964-107">Robust Programming</span></span>  
 <span data-ttu-id="bc964-108">Si le fichier existe déjà, il est remplacé.</span><span class="sxs-lookup"><span data-stu-id="bc964-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="bc964-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="bc964-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="bc964-110">Le chemin d'accès est mal formé.</span><span class="sxs-lookup"><span data-stu-id="bc964-110">The path name is malformed.</span></span> <span data-ttu-id="bc964-111">Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bc964-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="bc964-112">Le chemin est en lecture seule (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="bc964-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="bc964-113">Le nom du chemin est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="bc964-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="bc964-114">Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="bc964-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="bc964-115">Le chemin n’est pas valide (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="bc964-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="bc964-116">Le chemin n’est constitué que d’un signe deux-points « : » (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="bc964-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bc964-117">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bc964-117">.NET Framework Security</span></span>  
 <span data-ttu-id="bc964-118">Une <xref:System.Security.SecurityException> peut être levée dans les environnements de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="bc964-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="bc964-119">L’appel à la méthode <xref:System.IO.File.Create%2A> nécessite <xref:System.Security.Permissions.FileIOPermission>.</span><span class="sxs-lookup"><span data-stu-id="bc964-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="bc964-120">Une <xref:System.UnauthorizedAccessException> est levée si l’utilisateur n’est pas autorisé à créer le fichier.</span><span class="sxs-lookup"><span data-stu-id="bc964-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc964-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc964-121">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File.Create%2A>  
 [<span data-ttu-id="bc964-122">Utilisation de bibliothèques à partir de code d’un niveau de confiance partiel</span><span class="sxs-lookup"><span data-stu-id="bc964-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)  
 [<span data-ttu-id="bc964-123">Notions fondamentales de la sécurité d’accès du code</span><span class="sxs-lookup"><span data-stu-id="bc964-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
