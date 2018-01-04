---
title: "Comment : ajouter des contrôles à des Windows Forms"
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
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9075c93181b68828a307924259a9170c046baa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="88b1d-102">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88b1d-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="88b1d-103">La plupart des formulaires sont conçus en ajoutant des contrôles à la surface de l’écran pour définir une interface utilisateur (IU).</span><span class="sxs-lookup"><span data-stu-id="88b1d-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="88b1d-104">A *contrôle* est un composant d’un formulaire utilisé pour afficher des informations ou accepter l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="88b1d-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="88b1d-105">Pour plus d’informations sur les contrôles, consultez [des contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="88b1d-105">For more information about controls, see [Windows Forms Controls](../../../../docs/framework/winforms/controls/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88b1d-106">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="88b1d-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="88b1d-107">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="88b1d-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="88b1d-108">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="88b1d-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="88b1d-109">Pour dessiner un contrôle sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="88b1d-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="88b1d-110">Ouvrez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="88b1d-110">Open the form.</span></span> <span data-ttu-id="88b1d-111">Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="88b1d-111">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="88b1d-112">Dans le **boîte à outils**, cliquez sur le contrôle que vous souhaitez ajouter à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="88b1d-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="88b1d-113">Dans le formulaire, cliquez à l’endroit où le coin supérieur gauche du contrôle à localiser et faites glisser vers l’emplacement souhaité de l’angle inférieur droit du contrôle à localiser.</span><span class="sxs-lookup"><span data-stu-id="88b1d-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="88b1d-114">Le contrôle est ajouté au formulaire avec la taille et l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="88b1d-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88b1d-115">Chaque contrôle possède une taille par défaut définie.</span><span class="sxs-lookup"><span data-stu-id="88b1d-115">Each control has a default size defined.</span></span> <span data-ttu-id="88b1d-116">Vous pouvez ajouter un contrôle à votre formulaire dans la taille du contrôle par défaut en le faisant glisser à partir de la **boîte à outils** au formulaire.</span><span class="sxs-lookup"><span data-stu-id="88b1d-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="88b1d-117">Pour faire glisser un contrôle à un formulaire</span><span class="sxs-lookup"><span data-stu-id="88b1d-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="88b1d-118">Ouvrez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="88b1d-118">Open the form.</span></span> <span data-ttu-id="88b1d-119">Pour plus d’informations, consultez [Comment : afficher des Windows Forms dans le concepteur](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span><span class="sxs-lookup"><span data-stu-id="88b1d-119">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="88b1d-120">Dans le **boîte à outils**, cliquez sur le contrôle souhaité et faites-le glisser vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="88b1d-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="88b1d-121">Le contrôle est ajouté au formulaire à l’emplacement spécifié dans sa taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="88b1d-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88b1d-122">Vous pouvez double-cliquer sur un contrôle dans le **boîte à outils** pour l’ajouter à l’angle supérieur gauche du formulaire dans sa taille par défaut.</span><span class="sxs-lookup"><span data-stu-id="88b1d-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="88b1d-123">Vous pouvez également ajouter dynamiquement des contrôles à un formulaire au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="88b1d-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="88b1d-124">Dans l’exemple de code suivant, un <xref:System.Windows.Forms.TextBox> contrôle sera ajouté au formulaire quand un <xref:System.Windows.Forms.Button> un clic sur le contrôle.</span><span class="sxs-lookup"><span data-stu-id="88b1d-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88b1d-125">La procédure suivante requiert l’existence d’un formulaire avec un **bouton** contrôle, `Button1`déjà placé dessus.</span><span class="sxs-lookup"><span data-stu-id="88b1d-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="88b1d-126">Pour ajouter un contrôle à un formulaire par programmation</span><span class="sxs-lookup"><span data-stu-id="88b1d-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="88b1d-127">Dans la méthode qui gère du bouton `Click` événement au sein de la classe de votre formulaire, code d’insertion semblable au suivant pour ajouter une référence à la variable du contrôle, définissez du contrôle `Location`et ajouter le contrôle.</span><span class="sxs-lookup"><span data-stu-id="88b1d-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="88b1d-128">Vous pouvez également ajouter le code pour initialiser d’autres propriétés du contrôle.</span><span class="sxs-lookup"><span data-stu-id="88b1d-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="88b1d-129">Vous pouvez exposer votre ordinateur local à un risque de sécurité via le réseau en référençant un malveillant `UserControl`.</span><span class="sxs-lookup"><span data-stu-id="88b1d-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="88b1d-130">Il s’agit uniquement d’un problème dans le cas d’une personne malveillante, créer un contrôle personnalisé causer des dommages, suivi de vous ajouter par erreur à votre projet.</span><span class="sxs-lookup"><span data-stu-id="88b1d-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88b1d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88b1d-131">See Also</span></span>  
 [<span data-ttu-id="88b1d-132">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88b1d-132">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="88b1d-133">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88b1d-133">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="88b1d-134">Guide pratique pour redimensionner des contrôles sur des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88b1d-134">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [<span data-ttu-id="88b1d-135">Guide pratique pour définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88b1d-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="88b1d-136">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88b1d-136">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
