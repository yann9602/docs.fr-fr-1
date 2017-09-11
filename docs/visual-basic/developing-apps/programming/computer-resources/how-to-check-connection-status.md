---
title: "Guide pratique pour vérifier l'état de la connexion en Visual Basic"
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
- Web connections
- IsAvailable property, about IsAvailable
- connections, checking status
- connection status
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: 26
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
ms.openlocfilehash: a3654eb51bb47317c2dc7bf74979a847438b0ae8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="e803e-102">Guide pratique pour vérifier l'état de la connexion en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e803e-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="e803e-103">Vous pouvez utiliser la propriété <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> pour déterminer si l’ordinateur dispose d’une connexion Internet ou réseau active.</span><span class="sxs-lookup"><span data-stu-id="e803e-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="e803e-104">Pour vérifier si un ordinateur dispose d’une connexion active</span><span class="sxs-lookup"><span data-stu-id="e803e-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="e803e-105">Vérifiez si la propriété `IsAvailable` est `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="e803e-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="e803e-106">Le code suivant vérifie l’état de la propriété et le signale :</span><span class="sxs-lookup"><span data-stu-id="e803e-106">The following code checks the property's status and reports it:</span></span>  
  
     <span data-ttu-id="e803e-107">[!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e803e-107">[!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]</span></span>  
  
     <span data-ttu-id="e803e-108">Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e803e-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="e803e-109">Dans le sélecteur d’extraits de code, il se trouve sous **Connectivité et réseau**.</span><span class="sxs-lookup"><span data-stu-id="e803e-109">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="e803e-110">Pour plus d’informations, consultez [Extraits de code](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="e803e-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e803e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e803e-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A>

