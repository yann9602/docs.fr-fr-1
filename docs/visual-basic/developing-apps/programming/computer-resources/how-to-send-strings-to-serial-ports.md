---
title: "Guide pratique pour envoyer des chaînes aux ports série en Visual Basic"
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
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
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
ms.openlocfilehash: 602b249d01252bbb1853ed02d9af86697d54b0a5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="89a25-102">Guide pratique pour envoyer des chaînes aux ports série en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89a25-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="89a25-103">Cette rubrique explique comment utiliser `My.Computer.Ports` pour envoyer des chaînes aux ports série de l’ordinateur en [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="89a25-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="89a25-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="89a25-104">Example</span></span>  
 <span data-ttu-id="89a25-105">Cet exemple envoie une chaîne au port série COM1.</span><span class="sxs-lookup"><span data-stu-id="89a25-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="89a25-106">Vous devrez peut-être utiliser un autre port série de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="89a25-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="89a25-107">Utilisez la méthode `My.Computer.Ports.OpenSerialPort` pour obtenir une référence au port.</span><span class="sxs-lookup"><span data-stu-id="89a25-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="89a25-108">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="89a25-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="89a25-109">Le bloc `Using` permet à l’application de fermer le port série, même si cela génère une exception.</span><span class="sxs-lookup"><span data-stu-id="89a25-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="89a25-110">Tout le code qui manipule le port série doit apparaître dans ce bloc, ou dans un bloc `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="89a25-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="89a25-111">La méthode <xref:System.IO.Ports.SerialPort.WriteLine%2A> envoie les données au port série.</span><span class="sxs-lookup"><span data-stu-id="89a25-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 <span data-ttu-id="89a25-112">[!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="89a25-112">[!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89a25-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="89a25-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="89a25-114">Cet exemple suppose que l’ordinateur utilise `COM1`.</span><span class="sxs-lookup"><span data-stu-id="89a25-114">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="89a25-115">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="89a25-115">Robust Programming</span></span>  
 <span data-ttu-id="89a25-116">Cet exemple suppose que l’ordinateur utilise `COM1`. Pour plus de souplesse, le code doit autoriser l’utilisateur à sélectionner le port série dans la liste des ports disponibles.</span><span class="sxs-lookup"><span data-stu-id="89a25-116">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="89a25-117">Pour plus d’informations, consultez [Guide pratique pour afficher les ports série disponibles](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="89a25-117">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="89a25-118">Cet exemple utilise un bloc `Using` pour garantir que l’application ferme le port même si elle lève une exception.</span><span class="sxs-lookup"><span data-stu-id="89a25-118">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="89a25-119">Pour plus d’informations, consultez [using, instruction](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="89a25-119">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a25-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89a25-120">See Also</span></span>  
 <span data-ttu-id="89a25-121"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="89a25-121"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="89a25-122"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="89a25-122"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span></span>   
 <span data-ttu-id="89a25-123">[Guide pratique pour passer des appels avec des modems attachés aux ports série](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="89a25-123">[How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span></span>  
 [<span data-ttu-id="89a25-124">Guide pratique : afficher les ports série disponibles</span><span class="sxs-lookup"><span data-stu-id="89a25-124">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

