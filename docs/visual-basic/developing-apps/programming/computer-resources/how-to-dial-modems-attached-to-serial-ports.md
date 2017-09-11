---
title: "Guide pratique pour passer des appels avec des modems attachés aux ports série dans Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- modems, dialing
- serial ports, dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0daaf35cdebac3d69ddc536124d4c86b96955b11
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="d520e-102">Guide pratique pour passer des appels avec des modems attachés aux ports série dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d520e-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="d520e-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour passer un appel avec un modem dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d520e-103">This topic describes how to use `My.Computer.Ports` to dial a modem in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="d520e-104">En règle générale, le modem est connecté à l’un des ports série sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d520e-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="d520e-105">Pour que l’application puisse communiquer avec le modem, elle doit envoyer des commandes au port série approprié.</span><span class="sxs-lookup"><span data-stu-id="d520e-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="d520e-106">Pour communiquer avec un modem</span><span class="sxs-lookup"><span data-stu-id="d520e-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="d520e-107">Déterminez le port série auquel le modem est connecté.</span><span class="sxs-lookup"><span data-stu-id="d520e-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="d520e-108">Cet exemple part du principe que le modem est connecté à COM1.</span><span class="sxs-lookup"><span data-stu-id="d520e-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="d520e-109">Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.</span><span class="sxs-lookup"><span data-stu-id="d520e-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="d520e-110">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="d520e-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="d520e-111">Le bloc `Using` permet à l’application de fermer le port série, même si cela génère une exception.</span><span class="sxs-lookup"><span data-stu-id="d520e-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="d520e-112">Tout le code qui manipule le port série doit apparaître dans ce bloc, ou dans un bloc `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="d520e-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     <span data-ttu-id="d520e-113">[!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d520e-113">[!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]</span></span>  
  
3.  <span data-ttu-id="d520e-114">Définissez la propriété `DtrEnable` pour indiquer que l’ordinateur est prêt à accepter une transmission en provenance du modem.</span><span class="sxs-lookup"><span data-stu-id="d520e-114">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     <span data-ttu-id="d520e-115">[!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d520e-115">[!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]</span></span>  
  
4.  <span data-ttu-id="d520e-116">Envoyez la commande de numérotation et le numéro de téléphone au modem par l’intermédiaire du port série à l’aide de la méthode <xref:System.IO.Ports.SerialPort.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="d520e-116">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     <span data-ttu-id="d520e-117">[!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d520e-117">[!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d520e-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="d520e-118">Example</span></span>  
 <span data-ttu-id="d520e-119">[!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d520e-119">[!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]</span></span>  
  
 <span data-ttu-id="d520e-120">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="d520e-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="d520e-121">Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**.</span><span class="sxs-lookup"><span data-stu-id="d520e-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="d520e-122">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="d520e-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d520e-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d520e-123">Compiling the Code</span></span>  
 <span data-ttu-id="d520e-124">Cet exemple nécessite une référence à l’espace de noms <xref:System?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d520e-124">This example requires a reference to the <xref:System?displayProperty=fullName> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d520e-125">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d520e-125">Robust Programming</span></span>  
 <span data-ttu-id="d520e-126">Cet exemple part du principe que le modem est connecté à COM1.</span><span class="sxs-lookup"><span data-stu-id="d520e-126">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="d520e-127">Nous recommandons que le code autorise l’utilisateur à sélectionner le port série dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="d520e-127">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="d520e-128">Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="d520e-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="d520e-129">Cet exemple utilise un bloc `Using` pour garantir que l’application ferme le port même si elle lève une exception.</span><span class="sxs-lookup"><span data-stu-id="d520e-129">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="d520e-130">Pour plus d’informations, consultez [using, instruction](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d520e-130">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="d520e-131">Dans cet exemple, l’application déconnecte le port série après avoir utilisé le modem.</span><span class="sxs-lookup"><span data-stu-id="d520e-131">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="d520e-132">Dans la pratique, vous souhaiterez transférer des données vers et à partir du modem.</span><span class="sxs-lookup"><span data-stu-id="d520e-132">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="d520e-133">Pour plus d’informations, consultez [Guide pratique pour recevoir des chaînes des ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="d520e-133">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d520e-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d520e-134">See Also</span></span>  
 <span data-ttu-id="d520e-135"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="d520e-135"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="d520e-136"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d520e-136"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span></span>   
 <span data-ttu-id="d520e-137">[Guide pratique pour envoyer des chaînes aux ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="d520e-137">[How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span></span>  
 <span data-ttu-id="d520e-138">[Guide pratique pour recevoir des chaînes des ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="d520e-138">[How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md) </span></span>  
 [<span data-ttu-id="d520e-139">Guide pratique pour afficher les ports série disponibles</span><span class="sxs-lookup"><span data-stu-id="d520e-139">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

