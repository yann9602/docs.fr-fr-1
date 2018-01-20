---
title: "Comment : utiliser les modificateurs et les propriétés GenerateMember"
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
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f11595daac74ceb76c5d017af015d5523506bdf3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="db5b4-102">Comment : utiliser les modificateurs et les propriétés GenerateMember</span><span class="sxs-lookup"><span data-stu-id="db5b4-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="db5b4-103">Lorsque vous placez un composant sur un Windows Form, deux propriétés sont fournies par l’environnement de conception : `GenerateMember` et `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="db5b4-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="db5b4-104">Le `GenerateMember` propriété spécifie que lorsque le Concepteur Windows Forms génère une variable membre pour un composant.</span><span class="sxs-lookup"><span data-stu-id="db5b4-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="db5b4-105">Le `Modifiers` propriété est le modificateur d’accès assigné à cette variable de membre.</span><span class="sxs-lookup"><span data-stu-id="db5b4-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="db5b4-106">Si la valeur de la `GenerateMember` propriété `false`, la valeur de la `Modifiers` propriété n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="db5b4-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db5b4-107">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="db5b4-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="db5b4-108">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="db5b4-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="db5b4-109">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="db5b4-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="db5b4-110">Pour spécifier si un composant est un membre de l’écran</span><span class="sxs-lookup"><span data-stu-id="db5b4-110">To specify whether a component is a member of the form</span></span>  
  
1.  <span data-ttu-id="db5b4-111">Dans le Concepteur Windows Forms, ouvrez votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="db5b4-111">In the Windows Forms Designer, open your form.</span></span>  
  
2.  <span data-ttu-id="db5b4-112">Ouvrez le **boîte à outils**et sur le formulaire, placez trois <xref:System.Windows.Forms.Button> contrôles.</span><span class="sxs-lookup"><span data-stu-id="db5b4-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3.  <span data-ttu-id="db5b4-113">Définir le `GenerateMember` et `Modifiers` propriétés pour chaque <xref:System.Windows.Forms.Button> contrôle conformément au tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="db5b4-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="db5b4-114">Nom du bouton</span><span class="sxs-lookup"><span data-stu-id="db5b4-114">Button name</span></span>|<span data-ttu-id="db5b4-115">Valeur de GenerateMember</span><span class="sxs-lookup"><span data-stu-id="db5b4-115">GenerateMember value</span></span>|<span data-ttu-id="db5b4-116">Valeur de modificateurs</span><span class="sxs-lookup"><span data-stu-id="db5b4-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="db5b4-117">Aucune modification</span><span class="sxs-lookup"><span data-stu-id="db5b4-117">No change</span></span>|  
  
4.  <span data-ttu-id="db5b4-118">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="db5b4-118">Build the solution.</span></span>  
  
5.  <span data-ttu-id="db5b4-119">Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="db5b4-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6.  <span data-ttu-id="db5b4-120">Ouvrez le **Form1** nœud, puis, dans le **éditeur de Code**, ouvrez le **Form1.Designer.vb** ou **Form1.Designer.cs** fichier.</span><span class="sxs-lookup"><span data-stu-id="db5b4-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="db5b4-121">Ce fichier contient le code émis par le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="db5b4-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7.  <span data-ttu-id="db5b4-122">Recherchez les déclarations pour les trois boutons.</span><span class="sxs-lookup"><span data-stu-id="db5b4-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="db5b4-123">L’exemple de code suivant montre les différences spécifiées par le `GenerateMember` et `Modifiers` propriétés.</span><span class="sxs-lookup"><span data-stu-id="db5b4-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="db5b4-124">Par défaut, le Concepteur Windows Forms assigne le `private` (`Friend` en Visual Basic) modificateur aux contrôles conteneur comme <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="db5b4-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="db5b4-125">Si votre base de <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Form> a un contrôle conteneur, il n’acceptera pas de nouveaux enfants dans les formulaires et contrôles hérités.</span><span class="sxs-lookup"><span data-stu-id="db5b4-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="db5b4-126">La solution consiste à modifier le modificateur du contrôle conteneur de base à `protected` ou `public`.</span><span class="sxs-lookup"><span data-stu-id="db5b4-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5b4-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db5b4-127">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="db5b4-128">Héritage visuel des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db5b4-128">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="db5b4-129">Procédure pas à pas : démonstration de l’héritage visuel</span><span class="sxs-lookup"><span data-stu-id="db5b4-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [<span data-ttu-id="db5b4-130">Comment : hériter des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db5b4-130">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
