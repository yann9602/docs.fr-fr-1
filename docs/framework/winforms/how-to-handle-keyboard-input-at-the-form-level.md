---
title: "Comment&#160;: g&#233;rer l&#39;entr&#233;e au clavier au niveau du formulaire | Microsoft Docs"
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
  - "entrée au clavier, au niveau formulaire"
  - "claviers, entrée au niveau formulaire"
  - "Windows Forms, gérer les entrées au clavier"
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: g&#233;rer l&#39;entr&#233;e au clavier au niveau du formulaire
Windows Forms offre la possibilité de gérer les messages de clavier au niveau du formulaire, avant que les messages n'atteignent un contrôle.  Cette rubrique montre comment procéder.  
  
### Pour gérer un message de clavier au niveau du formulaire  
  
-   Gérez l'événement <xref:System.Windows.Forms.Control.KeyPress> ou <xref:System.Windows.Forms.Control.KeyDown> du formulaire de démarrage et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Form.KeyPreview%2A> du formulaire pour que les messages de clavier soient reçus par le formulaire avant qu'ils atteignent les contrôles sur le formulaire.  L'exemple de code suivant gère l'événement <xref:System.Windows.Forms.Control.KeyPress> en détectant toutes les touches numériques et en consommant « 1 », « 4 » et « 7 ».  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## Exemple  
 L'exemple de code suivant est l'application complète pour l'exemple ci\-dessus.  L'application comprend un <xref:System.Windows.Forms.TextBox> avec plusieurs autres contrôles qui vous permettent de déplacer le focus hors du <xref:System.Windows.Forms.TextBox>.  L'événement <xref:System.Windows.Forms.Control.KeyPress> du <xref:System.Windows.Forms.Form> principal consomme « 1 », « 4 » et « 7 » et l'événement <xref:System.Windows.Forms.Control.KeyPress> du <xref:System.Windows.Forms.TextBox> consomme « 2 », « 5 » et « 8 » tout en affichant les touches restantes.  Comparez la sortie de <xref:System.Windows.Forms.MessageBox> quand vous appuyez sur une touche numérique pendant que le <xref:System.Windows.Forms.TextBox> a le focus avec la sortie de <xref:System.Windows.Forms.MessageBox> quand vous appuyez sur une touche numérique pendant que le focus est sur l'un des autres contrôles.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 [Entrée au clavier dans une application Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)