---
title: "Add Content to a Text Box Using UI Automation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adding content to text boxes"
  - "text boxes, adding content"
  - "UI Automation, adding content to text boxes"
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
caps.latest.revision: 13
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 13
---
# Add Content to a Text Box Using UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui veulent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.  Pour obtenir les informations les plus récentes sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient un exemple de code qui montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour insérer du texte dans une zone de texte à une ligne.  Une méthode alternative est fournie pour des contrôles de texte enrichi et multilignes où [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] n'est pas applicable.  En comparaison, l'exemple montre également comment utiliser les méthodes Win32 pour obtenir les mêmes résultats.  
  
## Exemple  
 L'exemple suivant parcourt une séquence de contrôles de texte dans une application cible.  Chaque contrôle de texte est testé pour voir si un objet <xref:System.Windows.Automation.ValuePattern> peut être obtenu par ce contrôle à l'aide de la méthode <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>.  Si le contrôle de texte prend en charge le <xref:System.Windows.Automation.ValuePattern>, la méthode <xref:System.Windows.Automation.ValuePattern.SetValue%2A> est utilisée pour insérer une chaîne définie par l'utilisateur dans le contrôle de texte.  Sinon, on utilise la méthode <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=fullName>.  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## Voir aussi  
 [TextPattern Insert Text Sample](http://msdn.microsoft.com/fr-fr/67353f93-7ee2-42f2-ab76-5c078cf6ca16)