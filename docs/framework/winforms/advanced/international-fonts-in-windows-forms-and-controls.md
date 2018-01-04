---
title: "Polices internationales pour les applications Windows Forms et les contrôles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7b6574e452faf4f0396f7633ba7f21519948262
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="805a2-102">Polices internationales pour les applications Windows Forms et les contrôles</span><span class="sxs-lookup"><span data-stu-id="805a2-102">International Fonts in Windows Forms and Controls</span></span>
<span data-ttu-id="805a2-103">Dans les applications internationales la méthode de sélection des polices recommandée est d’utiliser la police de substitution autant que possible.</span><span class="sxs-lookup"><span data-stu-id="805a2-103">In International applications the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="805a2-104">Police de substitution signifie que le système détermine le script le caractère appartient.</span><span class="sxs-lookup"><span data-stu-id="805a2-104">Font fallback means that the system determines what script the character belongs to.</span></span>  
  
## <a name="using-font-fallback"></a><span data-ttu-id="805a2-105">À l’aide de la police de substitution</span><span class="sxs-lookup"><span data-stu-id="805a2-105">Using Font Fallback</span></span>  
 <span data-ttu-id="805a2-106">Pour tirer parti de cette fonctionnalité, ne définissez pas le <xref:System.Drawing.Font> propriété pour votre formulaire ou tout autre élément.</span><span class="sxs-lookup"><span data-stu-id="805a2-106">To take advantage of this feature, do not set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="805a2-107">L’application utilisera automatiquement la police système par défaut, ce qui diffère d’une langue localisée du système d’exploitation vers un autre.</span><span class="sxs-lookup"><span data-stu-id="805a2-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="805a2-108">Lorsque l’application s’exécute, le système fournit automatiquement la police correcte pour la culture sélectionnée dans le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="805a2-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>  
  
 <span data-ttu-id="805a2-109">Il existe une exception à la règle de ne pas définir la police, permettant de changer le style de police.</span><span class="sxs-lookup"><span data-stu-id="805a2-109">There is an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="805a2-110">Cela peut être important pour une application dans laquelle l’utilisateur clique sur un bouton pour afficher le texte dans une zone de texte en gras.</span><span class="sxs-lookup"><span data-stu-id="805a2-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="805a2-111">Pour ce faire, vous écririez une fonction pour modifier le style de police de la zone de texte à afficher en gras, en fonction de quelle que soit la police du formulaire.</span><span class="sxs-lookup"><span data-stu-id="805a2-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="805a2-112">Il est important d’appeler cette fonction à deux emplacements : dans du bouton <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements et dans le <xref:System.Windows.Forms.Control.FontChanged> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="805a2-112">It is important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="805a2-113">Si la fonction est appelée uniquement dans le <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements et un autre fragment de code modifie la famille de polices de l’intégralité du formulaire, la zone de texte ne changera pas avec le reste du formulaire.</span><span class="sxs-lookup"><span data-stu-id="805a2-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box will not change with the rest of the form.</span></span>  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 <span data-ttu-id="805a2-114">Toutefois, lorsque vous localisez votre application, la police en gras peut afficher mal pour certaines langues.</span><span class="sxs-lookup"><span data-stu-id="805a2-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="805a2-115">S’il s’agit d’un problème, vous souhaitez que les localisateurs doivent avoir la possibilité de basculer la police de gras au texte normal.</span><span class="sxs-lookup"><span data-stu-id="805a2-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="805a2-116">Étant donné que les localisateurs ne sont généralement pas les développeurs et n’ont pas accès au code source, uniquement aux fichiers de ressources, cette option doit être définie dans les fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="805a2-116">Since localizers are typically not developers and do not have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="805a2-117">Pour ce faire, vous devez définir le <xref:System.Drawing.Font.Bold%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="805a2-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="805a2-118">Ainsi, le paramètre de police qui est écrit dans les fichiers de ressources, où les localisateurs peuvent modifier.</span><span class="sxs-lookup"><span data-stu-id="805a2-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="805a2-119">Vous écrivez ensuite du code après le `InitializeComponent` méthode pour rétablir la police quelle que soit la police du formulaire est, en utilisant le style de police spécifié dans le fichier de ressources.</span><span class="sxs-lookup"><span data-stu-id="805a2-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a><span data-ttu-id="805a2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="805a2-120">See Also</span></span>  
 [<span data-ttu-id="805a2-121">Globalisation des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="805a2-121">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [<span data-ttu-id="805a2-122">Utilisation de polices et de texte</span><span class="sxs-lookup"><span data-stu-id="805a2-122">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
