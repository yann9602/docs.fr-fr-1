---
title: "Guide pratique pour récupérer le contenu du répertoire Mes documents en Visual Basic"
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
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: 13
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
ms.openlocfilehash: afe236c4b9245ac256fbcbf6bf453de5d706b80f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="63bb2-102">Guide pratique pour récupérer le contenu du répertoire Mes documents en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63bb2-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="63bb2-103">Vous pouvez utiliser l’objet <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> pour lire la plupart des répertoires de **Tous les utilisateurs**, tels que **Mes documents** ou **Bureau**.</span><span class="sxs-lookup"><span data-stu-id="63bb2-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="63bb2-104">Pour lire à partir du dossier Mes documents</span><span class="sxs-lookup"><span data-stu-id="63bb2-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="63bb2-105">Utilisez la méthode `ReadAllText` pour lire le texte de chaque fichier dans un répertoire spécifique.</span><span class="sxs-lookup"><span data-stu-id="63bb2-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="63bb2-106">Le code suivant spécifie un répertoire et un fichier, puis il utilise `ReadAllText` pour les lire dans la chaîne nommée `patients`.</span><span class="sxs-lookup"><span data-stu-id="63bb2-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     <span data-ttu-id="63bb2-107">[!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="63bb2-107">[!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63bb2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63bb2-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>

