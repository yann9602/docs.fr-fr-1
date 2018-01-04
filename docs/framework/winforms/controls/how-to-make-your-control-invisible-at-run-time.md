---
title: "Comment : rendre votre contrôle invisible au moment de l'exécution"
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
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e28a682c6f3bfc52a293daebeade960c1875bb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="e6455-102">Comment : rendre votre contrôle invisible au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="e6455-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="e6455-103">Il existe des cas lorsque vous souhaitez peut-être créer un contrôle utilisateur qui est invisible au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e6455-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="e6455-104">Par exemple, un contrôle réveil peut être invisible sauf lorsque le réveil sonne.</span><span class="sxs-lookup"><span data-stu-id="e6455-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="e6455-105">Cela est facilement réalisable en définissant le <xref:System.Windows.Forms.Control.Visible%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e6455-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="e6455-106">Si le <xref:System.Windows.Forms.Control.Visible%2A> propriété est `true`, votre contrôle apparaîtra normalement.</span><span class="sxs-lookup"><span data-stu-id="e6455-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="e6455-107">Si `false`, votre contrôle sera masqué.</span><span class="sxs-lookup"><span data-stu-id="e6455-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="e6455-108">Bien que le code de votre contrôle continue de s’exécuter invisible, vous ne serez pas en mesure d’interagir avec le contrôle via l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e6455-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="e6455-109">Si vous souhaitez créer un contrôle invisible qui continue de répondre aux entrées utilisateur (par exemple, les clics de souris), vous devez créer un contrôle transparent.</span><span class="sxs-lookup"><span data-stu-id="e6455-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="e6455-110">Pour plus d’informations, consultez [affectation un arrière-plan Transparent à votre contrôle](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="e6455-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="e6455-111">Pour rendre votre contrôle invisible au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="e6455-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="e6455-112">Affectez à la propriété <xref:System.Windows.Forms.Control.Visible%2A> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="e6455-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e6455-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6455-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="e6455-114">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e6455-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="e6455-115">Guide pratique pour affecter un arrière-plan transparent à votre contrôle</span><span class="sxs-lookup"><span data-stu-id="e6455-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
