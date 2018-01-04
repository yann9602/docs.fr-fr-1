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
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Comment : rendre votre contrôle invisible au moment de l'exécution
Il existe des cas lorsque vous souhaitez peut-être créer un contrôle utilisateur qui est invisible au moment de l’exécution. Par exemple, un contrôle réveil peut être invisible sauf lorsque le réveil sonne. Cela est facilement réalisable en définissant le <xref:System.Windows.Forms.Control.Visible%2A> propriété. Si le <xref:System.Windows.Forms.Control.Visible%2A> propriété est `true`, votre contrôle apparaîtra normalement. Si `false`, votre contrôle sera masqué. Bien que le code de votre contrôle continue de s’exécuter invisible, vous ne serez pas en mesure d’interagir avec le contrôle via l’interface utilisateur. Si vous souhaitez créer un contrôle invisible qui continue de répondre aux entrées utilisateur (par exemple, les clics de souris), vous devez créer un contrôle transparent. Pour plus d’informations, consultez [affectation un arrière-plan Transparent à votre contrôle](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>Pour rendre votre contrôle invisible au moment de l’exécution  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.Control.Visible%2A> la valeur `false`.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Guide pratique pour affecter un arrière-plan transparent à votre contrôle](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
