---
title: "Guide pratique pour recevoir des chaînes provenant des ports série en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a58ce248404bfe4d6c55bba741b332acd7fcbf5c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="e2d9a-102">Guide pratique pour recevoir des chaînes provenant des ports série en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2d9a-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="e2d9a-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour recevoir des chaînes provenant des ports série de l’ordinateur en [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2d9a-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="e2d9a-104">Pour recevoir des chaînes provenant d’un port série</span><span class="sxs-lookup"><span data-stu-id="e2d9a-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="e2d9a-105">Initialisez la chaîne de retour.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  <span data-ttu-id="e2d9a-106">Déterminez quel port série doit fournir les chaînes.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="e2d9a-107">Cet exemple suppose qu’il s’agit de `COM1`.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-107">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="e2d9a-108">Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="e2d9a-109">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="e2d9a-110">Le bloc `Try...Catch...Finally` permet à l’application de fermer le port série, même si cela génère une exception.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="e2d9a-111">Tout le code qui manipule le port série doit apparaître dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="e2d9a-112">Créez une boucle `Do` pour lire les lignes de texte jusqu’à ce que plus aucune ligne ne soit disponible.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  <span data-ttu-id="e2d9a-113">Utilisez la méthode <xref:System.IO.Ports.SerialPort.ReadLine> pour lire la ligne de texte disponible suivante à partir du port série.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  <span data-ttu-id="e2d9a-114">Utilisez une instruction `If` pour déterminer si la méthode <xref:System.IO.Ports.SerialPort.ReadLine> retourne `Nothing` (ce qui signifie qu’il n’y a plus de texte disponible).</span><span class="sxs-lookup"><span data-stu-id="e2d9a-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="e2d9a-115">Si elle retourne `Nothing`, quittez la boucle `Do`.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  <span data-ttu-id="e2d9a-116">Ajoutez un bloc `Else` à l’instruction `If` pour gérer la situation si la chaîne est lue.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="e2d9a-117">Le bloc ajoute la chaîne du port série à la chaîne de retour.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  <span data-ttu-id="e2d9a-118">Retourne la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="e2d9a-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2d9a-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 <span data-ttu-id="e2d9a-120">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e2d9a-121">Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="e2d9a-122">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e2d9a-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2d9a-123">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e2d9a-123">Compiling the Code</span></span>  
 <span data-ttu-id="e2d9a-124">Cet exemple suppose que l’ordinateur utilise `COM1`.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e2d9a-125">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e2d9a-125">Robust Programming</span></span>  
 <span data-ttu-id="e2d9a-126">Cet exemple suppose que l’ordinateur utilise `COM1`.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="e2d9a-127">Pour plus de souplesse, le code doit autoriser l’utilisateur à sélectionner le port série dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="e2d9a-128">Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="e2d9a-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="e2d9a-129">Cet exemple utilise un bloc `Try...Catch...Finally` pour garantir que l’application ferme le port et intercepte les exceptions d’expiration.</span><span class="sxs-lookup"><span data-stu-id="e2d9a-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="e2d9a-130">Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e2d9a-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d9a-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2d9a-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="e2d9a-132">Guide pratique : passer des appels avec des modems attachés aux ports série</span><span class="sxs-lookup"><span data-stu-id="e2d9a-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="e2d9a-133">Guide pratique : envoyer des chaînes aux ports série</span><span class="sxs-lookup"><span data-stu-id="e2d9a-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="e2d9a-134">Guide pratique : afficher les ports série disponibles</span><span class="sxs-lookup"><span data-stu-id="e2d9a-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
