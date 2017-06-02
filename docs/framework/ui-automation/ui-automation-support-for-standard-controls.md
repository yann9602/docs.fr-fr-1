---
title: "UI Automation Support for Standard Controls | Microsoft Docs"
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
  - "controls, UI Automation support for"
  - "UI Automation, support for standard controls"
ms.assetid: 3770ea8a-2655-4add-9c59-fe0610ad5084
caps.latest.revision: 11
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 10
---
# UI Automation Support for Standard Controls
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient des informations sur la prise en charge d’[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pour les contrôles standard dans les applications développées pour les infrastructures [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] et [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Windows_Presentation_Foundation_Controls"></a>   
## Contrôles Windows Presentation Foundation  
 Tous les éléments du contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui fournissent des informations ou une prise en charge pour l’interaction utilisateur disposent d’une prise en charge native complète de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. D’autres éléments, tels que les panneaux, ne sont pas visibles par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Win32_Controls"></a>   
## Contrôles Win32  
 La plupart des contrôles [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 La prise en charge complète n’est fournie que pour les contrôles de la version 6 de ComCtrl32.dll \(disponible avec [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)] et les versions ultérieures\).  
  
 Les contrôles suivants sont pris en charge.  
  
|Nom de classe|Type de contrôle|  
|-------------------|----------------------|  
|Bouton|Bouton|  
|Bouton|RadioButton|  
|Bouton|Regrouper|  
|Bouton|Case à cocher|  
|Bouton|Lien hypertexte|  
|Bouton|SplitButton|  
|Bouton|Case à cocher|  
|ComboBoxEx32|ComboBox|  
|ComboBox|ComboBox|  
|Modifier|Document|  
|Modifier|Modifier|  
|SysLink|Lien hypertexte|  
|Statique|Texte|  
|Statique|Image|  
|SysIPAddress32|Personnalisé|  
|SysHeader32|Header\/HeaderItem|  
|SysListView32|DataGrid|  
|SysListView32|Liste|  
|ListBox|Liste|  
|ListBox|ListItem|  
|\#32768|Menu|  
|\#32768|MenuItem|  
|msctls\_progress32|Barre de progression|  
|RichEdit|Document. Consultez la remarque.|  
|RichEdit20A|Document|  
|RichEdit20W|Document|  
|RichEdit50W|Document|  
|ScrollBar|Curseur|  
|msctls\_trackbar32|Curseur|  
|msctls\_updown32|Spinner|  
|msctls\_statusbar32|StatusBar|  
|SysTabControl32|Onglet|  
|SysTabControl32|TabItem|  
|ToolbarWindow32|ToolBar|  
|ToolbarWindow32|MenuItem|  
|ToolbarWindow32|Bouton|  
|ToolbarWindow32|Case à cocher|  
|ToolbarWindow32|RadioButton|  
|ToolbarWindow32|Séparateur|  
|tooltips\_class32|Info\-bulle|  
|\#32774|Info\-bulle|  
|ReBarWindow32|ToolBar|  
|SysTreeView32|Arborescence|  
|SysTreeView32|TreeItem|  
  
 **Remarque** Le contrôle RichEdit est pris en charge uniquement pour les versions fournies avec [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] \(dans RichEd20.dll version 3.1 et version ultérieure, ainsi que dans MsftEdit.dll version 4.1 et version ultérieure\).  
  
 Les contrôles suivants ne sont pas pris en charge.  
  
|Nom de classe|Type du contrôle|  
|-------------------|----------------------|  
|SysAnimate32|Image|  
|SysPager|Spinner|  
|SysDateTimePick32|Personnalisé|  
|SysMonthCal32|Calendrier|  
|MS\_WINNOTE|Info\-bulle|  
|VBBubble|Info\-bulle|  
|ScrollBar \(quand il est utilisé comme contrôle autonome\)|Curseur|  
|SuperGrid|Personnalisé|  
  
<a name="Windows_Forms_Controls"></a>   
## contrôles Windows Forms  
 Les contrôles [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] via des fournisseurs côté client dans UIAutomationClientsideProviders.dll. Cet assembly est inscrit automatiquement pour être utilisé avec les applications clientes UI Automation.  
  
 En règle générale, les contrôles [!INCLUDE[TLA2#tla_winforms](../../../includes/tla2sharptla-winforms-md.md)] qui constituent des wrappers managés pour les contrôles communs [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], sont pris en charge par [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Les contrôles suivants sont pris en charge.  
  
|Nom de la classe|  
|----------------------|  
|Bouton|  
|Case à cocher|  
|CheckedListBox|  
|ColorDialog|  
|ComboBox|  
|FolderBrowser|  
|FontDialog|  
|GroupBox|  
|HscrollBar|  
|ImageList|  
|Label|  
|ListBox|  
|Affichage de liste|  
|MainMenu\/ContextMenu|  
|MonthCalendar|  
|NotifyIcon|  
|OpenFileDialog|  
|PageSetupDialog|  
|PrintDialog|  
|Barre de progression|  
|RadioButton|  
|RichTextBox|  
|SaveFileDialog|  
|ScrollableControl|  
|SoundPlayer|  
|StatusBar|  
|TabControl\/TabPage|  
|TextBox|  
|Minuterie|  
|ToolBar|  
|Info\-bulle|  
|TrackBar|  
|TreeView|  
|VscrollBar|  
|Navigateur web|  
  
 Les contrôles suivants sont exposés à [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] uniquement via leur prise en charge de [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. Certaines fonctionnalités ne sont peut\-être pas disponibles.  
  
|Nom du contrôle|  
|---------------------|  
|BindingSource|  
|DataGrid|  
|DataGridView|  
|DataNavigator|  
|DomainUpDown|  
|ErrorProvider|  
|FlowLayoutPanel|  
|Formulaire|  
|LinkLabel|  
|HelpProvider|  
|MaskedTextBox|  
|MenuStrip\/ContextMenuStrip|  
|NumericUpDown|  
|Volet|  
|PictureBox|  
|PrintDocument|  
|PrintPreviewControl|  
|PrintPreviewDialog|  
|PropertyGrid|  
|UserControl|  
|ToolStrip|  
|TableLayoutPanel|  
|SplitContainer\/SplitterPanel|  
|Séparateur|  
|RaftingContainer|  
|StatusStrip|  
  
## Voir aussi  
 [UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md)