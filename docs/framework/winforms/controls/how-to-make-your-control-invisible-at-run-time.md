---
title: "Comment&#160;: rendre votre contr&#244;le invisible au moment de l&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), rendre invisible au moment de l'exécution"
  - "contrôles personnalisés (Windows Forms), invisibles"
  - "contrôles invisibles"
  - "au moment de l'exécution, rendre les contrôles invisibles"
  - "contrôles utilisateur (Windows Forms), invisibles"
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: rendre votre contr&#244;le invisible au moment de l&#39;ex&#233;cution
Vous voudrez parfois créer un contrôle utilisateur qui soit invisible au moment de l'exécution.  Par exemple, un contrôle de réveil peut être invisible sauf lorsque le réveil sonne.  Cela est facilement réalisable en définissant la propriété <xref:System.Windows.Forms.Control.Visible%2A>.  Si cette <xref:System.Windows.Forms.Control.Visible%2A> propriété a la valeur `true`, votre contrôle apparaîtra normalement.  Si elle a la valeur `false`, votre contrôle sera masqué.  Bien que, même invisible, le code de votre contrôle continue de s'exécuter, vous ne pourrez pas interagir avec le contrôle par le biais de l'interface utilisateur.  Si vous souhaitez créer un contrôle invisible qui continue de répondre aux entrées utilisateur \(par exemple, les clics de souris\), vous devez créer un contrôle transparent.  Pour plus d'informations, consultez [Affectation d'un arrière\-plan transparent à votre contrôle](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).  
  
### Pour rendre votre contrôle invisible au moment de l'exécution  
  
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
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.Visible%2A>   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Comment : affecter un arrière\-plan transparent à votre contrôle](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)