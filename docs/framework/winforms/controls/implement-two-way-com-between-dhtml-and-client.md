---
title: "Comment : implémenter la communication bidirectionnelle entre le code DHTML et le code d'application cliente"
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
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63291cddc294b6ad8003636d6d79169f2d0852e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a><span data-ttu-id="b2641-102">Comment : implémenter la communication bidirectionnelle entre le code DHTML et le code d'application cliente</span><span class="sxs-lookup"><span data-stu-id="b2641-102">How to: Implement Two-Way Communication Between DHTML Code and Client Application Code</span></span>
<span data-ttu-id="b2641-103">Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.WebBrowser> pour ajouter du code d'application web dynamique HTML (DHTML) existant à vos applications clientes Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b2641-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to add existing dynamic HTML (DHTML) Web application code to your Windows Forms client applications.</span></span> <span data-ttu-id="b2641-104">Cela est utile quand vous avez consacré beaucoup de temps de développement à la création de contrôles DHTML et que vous souhaitez tirer parti des fonctionnalités d'interface utilisateur enrichies des Windows Forms sans avoir à réécrire le code existant.</span><span class="sxs-lookup"><span data-stu-id="b2641-104">This is useful when you have invested significant development time in creating DHTML-based controls and you want to take advantage of the rich user interface capabilities of Windows Forms without having to rewrite existing code.</span></span>  
  
 <span data-ttu-id="b2641-105">Le contrôle <xref:System.Windows.Forms.WebBrowser> vous permet d'implémenter la communication bidirectionnelle entre votre code d'application cliente et votre code de script de page web par le biais des propriétés <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> et <xref:System.Windows.Forms.WebBrowser.Document%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2641-105">The <xref:System.Windows.Forms.WebBrowser> control lets you implement two-way communication between your client application code and your Web page scripting code through the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> and <xref:System.Windows.Forms.WebBrowser.Document%2A> properties.</span></span> <span data-ttu-id="b2641-106">Vous pouvez aussi configurer le contrôle <xref:System.Windows.Forms.WebBrowser> pour que vos contrôles web fusionnent de façon homogène avec d'autres contrôles sur votre formulaire d'application, en masquant leur implémentation DHTML.</span><span class="sxs-lookup"><span data-stu-id="b2641-106">Additionally, you can configure the <xref:System.Windows.Forms.WebBrowser> control so that your Web controls blend seamlessly with other controls on your application form, hiding their DHTML implementation.</span></span> <span data-ttu-id="b2641-107">Pour fusionner les contrôles de façon homogène, mettez en forme la page affichée pour que sa couleur d'arrière-plan et le style visuel correspondent au reste du formulaire et utilisez les propriétés <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> et <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> pour désactiver les fonctionnalités standard du navigateur.</span><span class="sxs-lookup"><span data-stu-id="b2641-107">To seamlessly blend the controls, format the page displayed so that its background color and visual style match the rest of the form, and use the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, and <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> properties to disable standard browser features.</span></span>  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a><span data-ttu-id="b2641-108">Pour incorporer du code DHTML dans votre application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2641-108">To embed DHTML in your Windows Forms application</span></span>  
  
1.  <span data-ttu-id="b2641-109">Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> du contrôle <xref:System.Windows.Forms.WebBrowser> pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'ouvrir les fichiers qui sont déposés dessus.</span><span class="sxs-lookup"><span data-stu-id="b2641-109">Set the <xref:System.Windows.Forms.WebBrowser> control's <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  <span data-ttu-id="b2641-110">Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'afficher son menu contextuel quand l'utilisateur clique dessus avec le bouton droit de la souris.</span><span class="sxs-lookup"><span data-stu-id="b2641-110">Set the control's <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying its shortcut menu when the user right-clicks it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  <span data-ttu-id="b2641-111">Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> de répondre aux touches de raccourci.</span><span class="sxs-lookup"><span data-stu-id="b2641-111">Set the control's <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from responding to shortcut keys.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  <span data-ttu-id="b2641-112">Définissez la propriété <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> dans le constructeur du formulaire ou un gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.</span><span class="sxs-lookup"><span data-stu-id="b2641-112">Set the <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> property in the form's constructor or a <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
     <span data-ttu-id="b2641-113">Le code suivant utilise la classe de formulaire proprement dite pour l'objet de script.</span><span class="sxs-lookup"><span data-stu-id="b2641-113">The following code uses the form class itself for the scripting object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2641-114">Le modèle COM (Component Object Model) doit pouvoir accéder à l'objet de script.</span><span class="sxs-lookup"><span data-stu-id="b2641-114">Component Object Model (COM) must be able to access the scripting object.</span></span> <span data-ttu-id="b2641-115">Pour rendre votre formulaire visible par COM, ajoutez l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> à votre classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="b2641-115">To make your form visible to COM, add the <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribute to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  <span data-ttu-id="b2641-116">Implémentez dans votre code d'application des propriétés ou des méthodes publiques que votre code de script utilisera.</span><span class="sxs-lookup"><span data-stu-id="b2641-116">Implement public properties or methods in your application code that your script code will use.</span></span>  
  
     <span data-ttu-id="b2641-117">Par exemple, si vous utilisez la classe de formulaire pour l'objet de script, ajoutez le code suivant à votre classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="b2641-117">For example, if you use the form class for the scripting object, add the following code to your form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  <span data-ttu-id="b2641-118">Utilisez l'objet `window.external` dans votre code de script pour accéder aux propriétés et aux méthodes publiques de l'objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="b2641-118">Use the `window.external` object in your scripting code to access public properties and methods of the specified object.</span></span>  
  
     <span data-ttu-id="b2641-119">Le code HTML suivant montre comment appeler une méthode sur l'objet de script à partir d'un clic de bouton.</span><span class="sxs-lookup"><span data-stu-id="b2641-119">The following HTML code demonstrates how to call a method on the scripting object from a button click.</span></span> <span data-ttu-id="b2641-120">Copiez ce code dans l'élément BODY d'un document HTML que vous chargez à l'aide de la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> du contrôle ou que vous affectez à la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b2641-120">Copy this code into the BODY element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  <span data-ttu-id="b2641-121">Implémentez dans votre code de script des fonctions que votre code d'application utilisera.</span><span class="sxs-lookup"><span data-stu-id="b2641-121">Implement functions in your script code that your application code will use.</span></span>  
  
     <span data-ttu-id="b2641-122">L'élément HTML SCRIPT suivant fournit un exemple de fonction.</span><span class="sxs-lookup"><span data-stu-id="b2641-122">The following HTML SCRIPT element provides an example function.</span></span> <span data-ttu-id="b2641-123">Copiez ce code dans l'élément HEAD d'un document HTML que vous chargez à l'aide de la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> du contrôle ou que vous affectez à la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="b2641-123">Copy this code into the HEAD element of an HTML document that you load using the control's <xref:System.Windows.Forms.WebBrowser.Navigate%2A> method or that you assign to the control's <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property.</span></span>  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  <span data-ttu-id="b2641-124">Utilisez la propriété <xref:System.Windows.Forms.WebBrowser.Document%2A> pour accéder au code de script à partir de votre code d'application cliente.</span><span class="sxs-lookup"><span data-stu-id="b2641-124">Use the <xref:System.Windows.Forms.WebBrowser.Document%2A> property to access the script code from your client application code.</span></span>  
  
     <span data-ttu-id="b2641-125">Par exemple, ajoutez le code suivant à un gestionnaire d'événements de bouton <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="b2641-125">For example, add the following code to a button <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. <span data-ttu-id="b2641-126">Quand vous avez terminé de déboguer votre code DHTML, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'afficher des messages d'erreur pour les problèmes de code de script.</span><span class="sxs-lookup"><span data-stu-id="b2641-126">When you are finished debugging your DHTML, set the control's <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> property to `true` to prevent the <xref:System.Windows.Forms.WebBrowser> control from displaying error messages for script code problems.</span></span>  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="b2641-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2641-127">Example</span></span>  
 <span data-ttu-id="b2641-128">L’exemple de code complet suivant fournit une application de démonstration que vous pouvez utiliser pour comprendre cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b2641-128">The following complete code example provides a demonstration application that you can use to understand this feature.</span></span> <span data-ttu-id="b2641-129">Le code HTML est chargé dans le contrôle <xref:System.Windows.Forms.WebBrowser> via la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> au lieu d'être chargé à partir d'un fichier HTML distinct.</span><span class="sxs-lookup"><span data-stu-id="b2641-129">The HTML code is loaded into the <xref:System.Windows.Forms.WebBrowser> control through the <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> property instead of being loaded from a separate HTML file.</span></span>  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2641-130">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b2641-130">Compiling the Code</span></span>  
 <span data-ttu-id="b2641-131">Ce code nécessite :</span><span class="sxs-lookup"><span data-stu-id="b2641-131">This code requires:</span></span>  
  
-   <span data-ttu-id="b2641-132">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="b2641-132">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b2641-133">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b2641-133">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b2641-134">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="b2641-134">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="b2641-135">Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b2641-135">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2641-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2641-136">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b2641-137">WebBrowser, contrôle</span><span class="sxs-lookup"><span data-stu-id="b2641-137">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
