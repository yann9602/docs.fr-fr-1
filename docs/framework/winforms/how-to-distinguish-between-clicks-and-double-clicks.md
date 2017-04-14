---
title: "Comment&#160;: distinguer les clics des double-clics | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "clics de souris, différences entre simple clic et double clic"
  - "souris, clic"
  - "souris, double-clic"
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: distinguer les clics des double-clics
En règle générale, un *clic* unique lance une action d'interface utilisateur et un *double\-clic* étend l'action.  Par exemple, un clic sélectionne habituellement un élément et un double\-clic modifie l'élément sélectionné.  Toutefois, les événements de clic Windows Forms ne gèrent pas facilement les scénarios dans lesquels un clic et un double\-clic effectuent des actions incompatibles, car une action liée à l'événement <xref:System.Windows.Forms.Control.Click> ou <xref:System.Windows.Forms.Control.MouseClick> est effectuée avant l'action liée à l'événement <xref:System.Windows.Forms.Control.DoubleClick> ou <xref:System.Windows.Forms.Control.MouseDoubleClick>.  Cette rubrique illustre deux solutions à ce problème.  Une solution consiste à gérer l'événement de double\-clic et à annuler les actions dans la gestion de l'événement de clic.  Dans de rares cas, vous devrez peut\-être simuler le comportement de clic et de double\-clic en gérant l'événement <xref:System.Windows.Forms.Control.MouseDown> et en utilisant les propriétés <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> et <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> de la classe <xref:System.Windows.Forms.SystemInformation>.  Vous mesurez le délai entre les clics et si un deuxième clic se produit avant que la valeur de <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> soit atteinte et que le clic se trouve dans un rectangle défini par <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, vous exécutez l'action de double\-clic ; sinon, vous exécutez l'action de clic.  
  
### Pour annuler une action de clic  
  
-   Assurez\-vous que le contrôle que vous utilisez a un comportement de double\-clic standard.  Si ce n'est pas le cas, activez le contrôle avec la méthode <xref:System.Windows.Forms.Control.SetStyle%2A>.  Gérez l'événement de double\-clic et annulez les actions de clic et de double\-clic.  L'exemple de code suivant montre comment créer un bouton personnalisé avec double\-clic activé et comment annuler l'action de clic dans le code de gestion de l'événement de double\-clic.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### Pour faire la distinction entre les clics dans l'événement MouseDown  
  
-   Gérez l'événement <xref:System.Windows.Forms.Control.MouseDown> et déterminez l'emplacement et l'intervalle entre les clics à l'aide des propriétés <xref:System.Windows.Forms.SystemInformation> appropriées et d'un composant <xref:System.Windows.Forms.Timer>.  Exécutez l'action appropriée selon qu'un clic ou un double\-clic se produit.  L'exemple de code suivant montre comment procéder.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## Compilation du code  
 Ces exemples nécessitent :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de ces exemples à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer ces exemples dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en collant le code dans de nouveaux projets.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)