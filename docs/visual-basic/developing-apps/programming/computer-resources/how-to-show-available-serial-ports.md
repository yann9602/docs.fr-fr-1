---
title: "Guide pratique pour afficher les ports série disponibles en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1dc12d8ad4c27eff346ccb6a7f5fd2ae3bd76701
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="c05a6-102">Guide pratique pour afficher les ports série disponibles en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c05a6-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="c05a6-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour afficher les ports série qui sont disponibles sur l’ordinateur en [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c05a6-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="c05a6-104">Pour permettre à un utilisateur de sélectionner le port à utiliser, les noms des ports série sont placés dans un contrôle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="c05a6-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c05a6-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="c05a6-105">Example</span></span>  
 <span data-ttu-id="c05a6-106">Cet exemple exécute une boucle sur toutes les chaînes retournées par la propriété `My.Computer.Ports.SerialPortNames`.</span><span class="sxs-lookup"><span data-stu-id="c05a6-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="c05a6-107">Ces chaînes correspondent aux noms des ports série disponibles sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c05a6-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="c05a6-108">En règle générale, un utilisateur sélectionne le port série que l’application doit utiliser dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="c05a6-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="c05a6-109">Dans cet exemple, les noms de port série sont stockés dans un contrôle <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="c05a6-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="c05a6-110">Pour plus d’informations, consultez [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c05a6-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 <span data-ttu-id="c05a6-111">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c05a6-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c05a6-112">Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**.</span><span class="sxs-lookup"><span data-stu-id="c05a6-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="c05a6-113">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c05a6-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c05a6-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="c05a6-114">Compiling the Code</span></span>  
 <span data-ttu-id="c05a6-115">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="c05a6-115">This example requires:</span></span>  
  
-   <span data-ttu-id="c05a6-116">Une référence de projet à System.Windows.Forms.dll</span><span class="sxs-lookup"><span data-stu-id="c05a6-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="c05a6-117">Un accès aux membres de l’espace de noms <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="c05a6-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="c05a6-118">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c05a6-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c05a6-119">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c05a6-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="c05a6-120">Votre formulaire doit avoir un contrôle <xref:System.Windows.Forms.ListBox> nommé `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="c05a6-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c05a6-121">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="c05a6-121">Robust Programming</span></span>  
 <span data-ttu-id="c05a6-122">Vous n’avez pas besoin d’utiliser le contrôle <xref:System.Windows.Forms.ListBox> pour afficher les noms des ports série disponibles.</span><span class="sxs-lookup"><span data-stu-id="c05a6-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="c05a6-123">À la place, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.ComboBox> ou autre.</span><span class="sxs-lookup"><span data-stu-id="c05a6-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="c05a6-124">Si l’application n’a pas besoin d’une réponse de l’utilisateur, vous pouvez utiliser un contrôle <xref:System.Windows.Forms.TextBox> pour afficher les informations.</span><span class="sxs-lookup"><span data-stu-id="c05a6-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c05a6-125">Les noms de port retournés par `My.Computer.Ports.SerialPortNames` peuvent ne pas être corrects sur Windows 98.</span><span class="sxs-lookup"><span data-stu-id="c05a6-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="c05a6-126">Pour éviter les erreurs d’application, utilisez la gestion des exceptions, comme les instructions `Try...Catch...Finally` et `Using`, lorsque vous utilisez les noms de ports pour ouvrir des ports.</span><span class="sxs-lookup"><span data-stu-id="c05a6-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05a6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c05a6-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="c05a6-128">Guide pratique : passer des appels avec des modems attachés aux ports série</span><span class="sxs-lookup"><span data-stu-id="c05a6-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="c05a6-129">Guide pratique : envoyer des chaînes aux ports série</span><span class="sxs-lookup"><span data-stu-id="c05a6-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="c05a6-130">Guide pratique : recevoir des chaînes des ports série</span><span class="sxs-lookup"><span data-stu-id="c05a6-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
