---
title: "Vue d'ensemble du contrôle TextBox (Windows Forms)"
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
f1_keywords: TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="d1cef-102">Vue d'ensemble du contrôle TextBox (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d1cef-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="d1cef-103">Zones de texte Windows Forms sont utilisées pour obtenir des données à partir de l’utilisateur ou pour afficher le texte.</span><span class="sxs-lookup"><span data-stu-id="d1cef-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="d1cef-104">Le <xref:System.Windows.Forms.TextBox> contrôle est généralement utilisé pour le texte modifiable, bien qu’il puisse également être en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="d1cef-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="d1cef-105">Zones de texte peuvent afficher plusieurs lignes, renvoi à la taille du contrôle et ajouter une mise en forme.</span><span class="sxs-lookup"><span data-stu-id="d1cef-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="d1cef-106">Le <xref:System.Windows.Forms.TextBox> contrôle fournit un style de format unique pour le texte affiché ou entré dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d1cef-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="d1cef-107">Pour afficher plusieurs types de texte mis en forme, utilisez la <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="d1cef-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="d1cef-108">Pour plus d’informations, consultez [vue d’ensemble du contrôle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="d1cef-108">For more information, see [RichTextBox Control Overview](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="d1cef-109">Utilisation du contrôle de zone de texte</span><span class="sxs-lookup"><span data-stu-id="d1cef-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="d1cef-110">Le texte affiché par le contrôle est contenu dans le <xref:System.Windows.Forms.TextBox.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="d1cef-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="d1cef-111">Par défaut, vous pouvez entrer jusqu'à 2 048 caractères dans une zone de texte.</span><span class="sxs-lookup"><span data-stu-id="d1cef-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="d1cef-112">Si vous définissez la <xref:System.Windows.Forms.TextBox.Multiline%2A> propriété `true`, vous pouvez entrer jusqu'à 32 Ko de texte.</span><span class="sxs-lookup"><span data-stu-id="d1cef-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="d1cef-113">Le <xref:System.Windows.Forms.TextBox.Text%2A> propriété peut être définie au moment du design avec la fenêtre Propriétés, au moment de l’exécution dans le code ou par l’utilisateur au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1cef-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="d1cef-114">Le contenu actuel d’une zone de texte peut être récupéré au moment de l’exécution en lisant la <xref:System.Windows.Forms.TextBox.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="d1cef-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="d1cef-115">L’exemple de code suivant définit le texte dans le contrôle au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d1cef-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="d1cef-116">Le `InitializeMyControl` procédure s’exécutera pas automatiquement ; il doit être appelé.</span><span class="sxs-lookup"><span data-stu-id="d1cef-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1cef-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1cef-117">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="d1cef-118">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1cef-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d1cef-119">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1cef-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d1cef-120">Guide pratique pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="d1cef-120">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="d1cef-121">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="d1cef-121">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="d1cef-122">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1cef-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d1cef-123">Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1cef-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="d1cef-124">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="d1cef-124">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
