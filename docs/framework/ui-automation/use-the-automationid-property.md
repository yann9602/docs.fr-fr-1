---
title: "Use the AutomationID Property | Microsoft Docs"
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
  - "AutomationId property"
  - "UI Automation, AutomationId property"
  - "properties, AutomationId"
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
caps.latest.revision: 21
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 21
---
# Use the AutomationID Property
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient des scénarios et des exemples de code qui montrent comment et quand <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> peut être utilisé pour localiser un élément dans l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> identifie de manière unique un élément UI Automation parmi ses frères. Pour plus d’informations sur les identificateurs de propriété associés à l’identification du contrôle, consultez [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  La propriété <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> ne garantit pas une identité unique dans toute l’arborescence. Elle nécessite généralement un conteneur et des informations de portée pour être utile. Par exemple, une application peut contenir un contrôle de menu avec plusieurs éléments de menu de niveau supérieur qui, à leur tour, contiennent plusieurs éléments enfants. Ces éléments de menu secondaires peuvent être identifiés par un schéma générique tel que « Item1 », « Item2 » et ainsi de suite, qui autorise les identificateurs dupliqués pour les enfants dans l’ensemble des éléments de menu de niveau supérieur.  
  
## Scénarios  
 Trois scénarios principaux d’application cliente UI Automation ont été identifiés et nécessitent l’utilisation de <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> pour obtenir des résultats exacts et cohérents lors de la recherche d’éléments.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> est pris en charge par tous les éléments UI Automation dans l’affichage de contrôle, à l’exception des fenêtres d’application de niveau supérieur, des éléments UI Automation dérivés des contrôles [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] n’ayant pas d’ID ou de x:Uid, et des éléments UI Automation dérivés des contrôles [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] n’ayant pas d’ID de contrôle.  
  
#### Utiliser un AutomationID unique et détectable pour localiser un élément spécifique dans l’arborescence UI Automation  
  
-   Utilisez un outil comme [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] pour signaler la propriété <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> d’un élément [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] d’intérêt. Cette valeur peut ensuite être copiée et collée dans une application cliente telle qu’un script de test en vue de tests automatisés. Cette approche réduit et simplifie le code nécessaire pour identifier et localiser un élément au moment de l’exécution.  
  
> [!CAUTION]
>  En général, vous devez essayer d’obtenir uniquement les enfants directs de <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Une recherche des descendants peut itérer au sein de centaines ou de milliers d’éléments, ce qui peut provoquer un dépassement de capacité de la pile. Si vous tentez d’obtenir un élément spécifique de niveau inférieur, vous devez commencer votre recherche à partir de la fenêtre d’application ou d’un conteneur de niveau inférieur.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### Utiliser un chemin persistant pour revenir à un AutomationElement déjà identifié  
  
-   Les applications clientes, qu’il s’agisse de simples scripts de test ou de véritables utilitaires d’enregistrement et de lecture, peuvent nécessiter l’accès à des éléments qui ne sont pas actuellement instanciés, comme une boîte de dialogue d’ouverture de fichier ou un élément de menu, et qui donc n’existent pas dans l’arborescence UI Automation. Ces éléments ne peuvent être instanciés qu’en reproduisant, ou en « lisant », une séquence spécifique d’actions d’[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] à l’aide de propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] comme AutomationID, les modèles de contrôle et les écouteurs d’événements. Consultez [Test Script Generator Sample](http://msdn.microsoft.com/fr-fr/028467fd-2980-4691-9522-0131dcef23a0) pour obtenir un exemple qui utilise [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour générer des scripts de test en fonction de l’interaction de l’utilisateur avec l’[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### Utiliser un chemin relatif pour revenir à un AutomationElement déjà identifié  
  
-   Dans certaines circonstances, l’unicité d’AutomationID n’étant garantie que parmi ses frères, plusieurs éléments dans l’arborescence UI Automation peuvent avoir des valeurs de propriété AutomationID identiques. Dans ce cas, les éléments peuvent être identifiés de manière unique en fonction d’un parent et, si nécessaire, d’un grand\-parent. Par exemple, un développeur peut fournir une barre de menus avec plusieurs éléments de menu, chacun contenant plusieurs éléments de menu enfants dans lesquels les enfants sont identifiés avec des AutomationID séquentiels tels que « Item1 », « Item2 » et ainsi de suite. Chaque élément de menu peut ensuite être identifié de manière unique par son AutomationID accompagné de l’AutomationID de son parent et, si nécessaire, de son grand\-parent.  
  
## Voir aussi  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Find a UI Automation Element Based on a Property Condition](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)