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
# <a name="how-to-create-a-file-in-visual-basic"></a>Guide pratique pour créer un fichier en Visual Basic
Cet exemple crée un fichier texte vide à l’emplacement spécifié à l’aide de la méthode <xref:System.IO.File.Create%2A> de la classe <xref:System.IO.File>.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Utilisez la variable `file` pour écrire dans le fichier.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Si le fichier existe déjà, il est remplacé.  
  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le chemin d'accès est mal formé. Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).  
  
-   Le chemin est en lecture seule (<xref:System.IO.IOException>).  
  
-   Le nom du chemin est `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
-   Le chemin n’est pas valide (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Le chemin n’est constitué que d’un signe deux-points « : » (<xref:System.NotSupportedException>).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Une <xref:System.Security.SecurityException> peut être levée dans les environnements de confiance partielle.  
  
 L’appel à la méthode <xref:System.IO.File.Create%2A> nécessite <xref:System.Security.Permissions.FileIOPermission>.  
  
 Une <xref:System.UnauthorizedAccessException> est levée si l’utilisateur n’est pas autorisé à créer le fichier.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [Utilisation de bibliothèques à partir de code d’un niveau de confiance partiel](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)   
 [Notions fondamentales de la sécurité d’accès du code](https://msdn.microsoft.com/library/33tceax8)

