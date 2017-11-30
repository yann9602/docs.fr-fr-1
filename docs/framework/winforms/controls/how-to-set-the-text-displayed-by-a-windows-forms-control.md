---
title: "Comment : définir le texte affiché par un contrôle Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a81c2202400968b4d4c95b40de7476fbd68d6182
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a><span data-ttu-id="1dc28-102">Comment : définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dc28-102">How to: Set the Text Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="1dc28-103">Généralement, les contrôles Windows Forms affichent du texte en rapport avec la fonction principale du contrôle.</span><span class="sxs-lookup"><span data-stu-id="1dc28-103">Windows Forms controls usually display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="1dc28-104">Par exemple, un contrôle <xref:System.Windows.Forms.Button> affiche habituellement une légende indiquant l'action à exécuter quand le bouton est activé.</span><span class="sxs-lookup"><span data-stu-id="1dc28-104">For example, a <xref:System.Windows.Forms.Button> control usually displays a caption indicating what action will be performed when the button is clicked.</span></span> <span data-ttu-id="1dc28-105">Pour tous les contrôles, vous pouvez définir ou retourner le texte à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="1dc28-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="1dc28-106">Vous pouvez modifier la police en utilisant la propriété <xref:System.Windows.Forms.Control.Font%2A>.</span><span class="sxs-lookup"><span data-stu-id="1dc28-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span> <span data-ttu-id="1dc28-107">Vous pouvez également définir le texte à l'aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="1dc28-107">You can also set the text using the designer.</span></span>  <span data-ttu-id="1dc28-108">Consultez également [Comment : créer accès clés pour Windows Forms contrôles à l’aide du concepteur](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [Comment : définir le texte affiché par un contrôle Windows Forms à l’aide du concepteur](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [Comment : définir l’Image Affiché par un contrôle à l’aide du Concepteur Windows Forms](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1dc28-108">Also see [How to: Create Access Keys for Windows Forms Controls Using the Designer](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [How to: Set the Text Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [How to: Set the Image Displayed by a Windows Forms Control Using the Designer](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a><span data-ttu-id="1dc28-109">Pour définir le texte affiché par un contrôle par programmation</span><span class="sxs-lookup"><span data-stu-id="1dc28-109">To set the text displayed by a control programmatically</span></span>  
  
1.  <span data-ttu-id="1dc28-110">Affectez une chaîne comme valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="1dc28-110">Set the <xref:System.Windows.Forms.Control.Text%2A> property to a string.</span></span>  
  
     <span data-ttu-id="1dc28-111">Pour créer une touche d'accès soulignée, incluez une esperluette (&) avant la lettre qui sera la touche d'accès.</span><span class="sxs-lookup"><span data-stu-id="1dc28-111">To create an underlined access key, includes an ampersand (&) before the letter that will be the access key.</span></span>  
  
2.  <span data-ttu-id="1dc28-112">Affectez un objet de type <xref:System.Drawing.Font> comme valeur de la propriété <xref:System.Windows.Forms.Control.Font%2A>.</span><span class="sxs-lookup"><span data-stu-id="1dc28-112">Set the <xref:System.Windows.Forms.Control.Font%2A> property to an object of type <xref:System.Drawing.Font>.</span></span>  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1dc28-113">Vous pouvez utiliser un caractère d'échappement pour afficher un caractère spécial dans des éléments d'interface utilisateur qui l'interpréteraient normalement différemment, tels que des éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="1dc28-113">You can use an escape character to display a special character in user-interface elements that would normally interpret them differently, such as menu items.</span></span> <span data-ttu-id="1dc28-114">Par exemple, la ligne de code suivante définit le texte de l'élément de menu pour qu'il indique « & Now For Something Completely Different » :</span><span class="sxs-lookup"><span data-stu-id="1dc28-114">For example, the following line of code sets the menu item's text to read "& Now For Something Completely Different":</span></span>  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1dc28-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dc28-115">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1dc28-116">Guide pratique pour créer des touches d'accès rapide pour des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dc28-116">How to: Create Access Keys for Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [<span data-ttu-id="1dc28-117">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1dc28-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
