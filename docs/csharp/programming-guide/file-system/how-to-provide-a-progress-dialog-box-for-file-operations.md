---
title: "Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ac68b5aa6014db87b4f7a269ef73d0608371bd8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="10dcc-102">Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="10dcc-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="10dcc-103">Vous pouvez fournir une boîte de dialogue standard qui montre la progression des opérations sur les fichiers dans Windows si vous utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> de l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="10dcc-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="10dcc-104">Pour ajouter une référence dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10dcc-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="10dcc-105">Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="10dcc-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="10dcc-106">La boîte de dialogue **Gestionnaire de références** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="10dcc-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="10dcc-107">Dans la zone **Assemblys**, choisissez **Framework** si ce n’est pas sélectionné.</span><span class="sxs-lookup"><span data-stu-id="10dcc-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="10dcc-108">Dans la liste des noms, cochez la case **Microsoft.VisualBasic**, puis choisissez le bouton **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="10dcc-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10dcc-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="10dcc-109">Example</span></span>  
 <span data-ttu-id="10dcc-110">Le code suivant copie le répertoire spécifié par `sourcePath` dans le répertoire spécifié par `destinationPath`.</span><span class="sxs-lookup"><span data-stu-id="10dcc-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="10dcc-111">Ce code fournit également une boîte de dialogue standard qui affiche une estimation du temps restant avant la fin de l’opération.</span><span class="sxs-lookup"><span data-stu-id="10dcc-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="10dcc-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10dcc-112">See Also</span></span>  
 [<span data-ttu-id="10dcc-113">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="10dcc-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
