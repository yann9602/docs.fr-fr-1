---
title: "Comment : créer une zone de texte en lecture seule (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9cf6064442c3b648116f98f98f169dac12e5e88c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a><span data-ttu-id="d62df-102">Comment : créer une zone de texte en lecture seule (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d62df-102">How to: Create a Read-Only Text Box (Windows Forms)</span></span>
<span data-ttu-id="d62df-103">Vous pouvez transformer une zone de texte Windows Forms modifiable dans un contrôle en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d62df-103">You can transform an editable Windows Forms text box into a read-only control.</span></span> <span data-ttu-id="d62df-104">Par exemple, la zone de texte peut afficher une valeur qui est généralement modifiée mais n’est pas actuellement, en raison de l’état de l’application.</span><span class="sxs-lookup"><span data-stu-id="d62df-104">For example, the text box may display a value that is usually edited but may not be currently, due to the state of the application.</span></span>  
  
### <a name="to-create-a-read-only-text-box"></a><span data-ttu-id="d62df-105">Pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="d62df-105">To create a read-only text box</span></span>  
  
1.  <span data-ttu-id="d62df-106">Définir le <xref:System.Windows.Forms.TextBox> du contrôle <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="d62df-106">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property to `true`.</span></span> <span data-ttu-id="d62df-107">Avec la propriété `true`, les utilisateurs peuvent toujours faire défiler et mettre en surbrillance du texte dans une zone de texte sans autoriser de modification.</span><span class="sxs-lookup"><span data-stu-id="d62df-107">With the property set to `true`, users can still scroll and highlight text in a text box without allowing changes.</span></span> <span data-ttu-id="d62df-108">A **copie** commande est fonctionnelle dans une zone de texte, mais **couper** et **coller** commandes ne sont pas.</span><span class="sxs-lookup"><span data-stu-id="d62df-108">A **Copy** command is functional in a text box, but **Cut** and **Paste** commands are not.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d62df-109">Le <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriété affecte uniquement l’interaction utilisateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d62df-109">The <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> property only affects user interaction at run time.</span></span> <span data-ttu-id="d62df-110">Vous pouvez toujours modifier contenu des zones de texte par programme au moment de l’exécution en modifiant le <xref:System.Windows.Forms.TextBox.Text%2A> propriété de la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="d62df-110">You can still change text box contents programmatically at run time by changing the <xref:System.Windows.Forms.TextBox.Text%2A> property of the text box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62df-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d62df-111">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="d62df-112">Vue d’ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="d62df-112">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="d62df-113">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d62df-113">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d62df-114">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d62df-114">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d62df-115">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="d62df-115">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="d62df-116">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d62df-116">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d62df-117">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d62df-117">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d62df-118">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="d62df-118">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
