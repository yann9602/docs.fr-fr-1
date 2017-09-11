---
title: "Comment : écrire des messages de journal (Visual Basic)"
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
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffc45b93250ba9e909776352b702be2e8295435d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="c5fd0-102">Comment : écrire des messages de journal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5fd0-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="c5fd0-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur votre application.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="c5fd0-104">Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` pour enregistrer des informations de traçage.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="c5fd0-105">Pour enregistrer des informations sur les exceptions, utilisez la méthode `My.Application.Log.WriteException`. Consultez [Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="c5fd0-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5fd0-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5fd0-106">Example</span></span>  
 <span data-ttu-id="c5fd0-107">Cet exemple utilise la méthode `My.Application.Log.WriteEntry` pour écrire les informations de traçage.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 <span data-ttu-id="c5fd0-108">[!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c5fd0-108">[!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c5fd0-109">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c5fd0-109">.NET Framework Security</span></span>  
 <span data-ttu-id="c5fd0-110">Vérifiez que les données que vous écrivez dans le journal n’incluent pas d’informations sensibles, comme des mots de passe utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c5fd0-110">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="c5fd0-111">Pour plus d’informations, consultez [Utilisation des journaux d’application](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="c5fd0-111">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fd0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5fd0-112">See Also</span></span>  
 <span data-ttu-id="c5fd0-113"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c5fd0-113"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="c5fd0-114"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="c5fd0-114"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="c5fd0-115"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="c5fd0-115"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="c5fd0-116">[Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="c5fd0-116">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="c5fd0-117">[Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="c5fd0-117">[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span></span>  
 <span data-ttu-id="c5fd0-118">[Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="c5fd0-118">[Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span></span>  
 <span data-ttu-id="c5fd0-119">[Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="c5fd0-119">[Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span></span>  
 [<span data-ttu-id="c5fd0-120">Procédure pas à pas : filtrage de la sortie de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c5fd0-120">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

