---
title: "Obtain Mixed Text Attribute Details Using UI Automation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
caps.latest.revision: 11
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 11
---
# Obtain Mixed Text Attribute Details Using UI Automation
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique montre comment utiliser [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour obtenir des détails d’attribut de texte à partir d’une plage de texte qui couvre plusieurs valeurs d’attribut. Une plage de texte peut correspondre à l’emplacement actuel du signe insertion \(ou de la sélection dégénérée\) dans un document, une sélection contiguë de texte, une collection de sélections disjointes de texte ou l’ensemble du contenu textuel d’un document.  
  
## Exemple  
 L’exemple de code suivant montre comment obtenir le <xref:System.Windows.Automation.TextPattern.FontNameAttribute> d’une plage de texte où <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> retourne un objet <xref:System.Windows.Automation.TextPattern.MixedAttributeValue>.  
  
 [!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
 [!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 Le modèle de contrôle <xref:System.Windows.Automation.TextPattern>, associé à la classe <xref:System.Windows.Automation.Text.TextPatternRange>, prend en charge les attributs de texte, les propriétés et les méthodes de base. Pour les fonctionnalités spécifiques au contrôle qui ne sont pas prises en charge par <xref:System.Windows.Automation.TextPattern> or <xref:System.Windows.Automation.Text.TextPatternRange>, la classe <xref:System.Windows.Automation.AutomationElement> fournit des méthodes permettant à un client UI Automation d’accéder au modèle objet natif correspondant.  
  
## Voir aussi  
 [UI Automation TextPattern Overview](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)   
 [Add Content to a Text Box Using UI Automation](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)   
 [Find and Highlight Text Using UI Automation](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)   
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [Obtain Text Attributes Using UI Automation](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)