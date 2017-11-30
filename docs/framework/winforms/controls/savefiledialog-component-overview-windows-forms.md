---
title: Vue d'ensemble du composant SaveFileDialog (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cbdc1cb96234e302458cbeac6d6ae26b63c956e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="e4ed6-102">Vue d'ensemble du composant SaveFileDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e4ed6-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e4ed6-103">Le composant Windows Forms <xref:System.Windows.Forms.SaveFileDialog>  est une boîte de dialogue préconfigurée.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="e4ed6-104">Il est identique à la norme **enregistrer le fichier** boîte de dialogue utilisée par Windows.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="e4ed6-105">Il hérite de la classe <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="e4ed6-106">Utilisation du composant SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="e4ed6-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="e4ed6-107">Utilisez-le comme une solution simple pour permettre aux utilisateurs d’enregistrer des fichiers au lieu de configurer votre propre boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="e4ed6-108">En vous appuyant sur des boîtes de dialogue Windows standard, les fonctionnalités de base des applications que vous créez sont immédiatement familière aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="e4ed6-109">Sachez, toutefois, qui une fois à l’aide de la <xref:System.Windows.Forms.SaveFileDialog> composant, vous devez écrire votre propre logique d’enregistrement du fichier.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="e4ed6-110">Vous pouvez utiliser la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode pour afficher la boîte de dialogue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="e4ed6-111">Vous pouvez ouvrir un fichier dans le mode de lecture/écriture à l’aide du <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="e4ed6-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="e4ed6-112">Lorsqu’il est ajouté à un formulaire, le <xref:System.Windows.Forms.SaveFileDialog> composant apparaît dans la barre d’état en bas du Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4ed6-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ed6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4ed6-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="e4ed6-114">SaveFileDialog, composant</span><span class="sxs-lookup"><span data-stu-id="e4ed6-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
