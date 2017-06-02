---
title: "Vue d&#39;ensemble de la propri&#233;t&#233; AutoSize | Microsoft Docs"
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
  - "dimensionnement automatique"
  - "AutoSize (propriété)"
  - "AutoSizeMode (propriété)"
  - "disposition (Windows Forms), AutoSize"
  - "dimensionner, automatique"
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble de la propri&#233;t&#233; AutoSize
La propriété <xref:System.Windows.Forms.Control.AutoSize%2A> permet à un contrôle de modifier sa taille, si nécessaire, pour atteindre la valeur spécifiée par la propriété <xref:System.Windows.Forms.Control.PreferredSize%2A>.  Vous ajustez le comportement de dimensionnement de contrôles spécifiques en définissant la propriété `AutoSizeMode`.  
  
## Comportement de redimensionnement automatique  
 Seuls certains contrôles prennent en charge la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.  De plus, quelques contrôles qui prennent en charge la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> prennent en charge également la propriété `AutoSizeMode`.  
  
 La propriété <xref:System.Windows.Forms.Control.AutoSize%2A> produit un comportement quelque peu différent, selon le type de contrôle spécifique et la valeur de la propriété `AutoSizeMode`, si la propriété existe.  Le tableau suivant décrit les comportements qui sont toujours vrais et fournit une brève description de chacun :  
  
|Comportement toujours vrai|Description|  
|--------------------------------|-----------------|  
|Le dimensionnement automatique est une fonctionnalité runtime.|Cela signifie qu'il n'augmente jamais ou réduit la taille d'un contrôle, puis n'a aucun plus effet supplémentaire.|  
|Si un contrôle change de taille, la valeur de sa propriété <xref:System.Windows.Forms.Control.Location%2A> reste toujours constante.|Lorsque le contenu d'un contrôle fait augmenter la taille de celui\-ci, le contrôle se développe vers la droite et le bas.  Les contrôles ne se développent pas à gauche.|  
|Les propriétés <xref:System.Windows.Forms.Control.Dock%2A> et <xref:System.Windows.Forms.Control.Anchor%2A> sont honorées lorsque <xref:System.Windows.Forms.Control.AutoSize%2A> a la valeur `true`.|La valeur de la propriété <xref:System.Windows.Forms.Control.Location%2A> du contrôle s'ajuste à la valeur correcte.<br /><br /> **Remarque** Le contrôle <xref:System.Windows.Forms.Label> est l'exception à cette règle.  Lorsque vous attribuez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> d'un contrôle ancré <xref:System.Windows.Forms.Label> la valeur `true`, le contrôle <xref:System.Windows.Forms.Label> ne s'étire pas.|  
|Les propriétés <xref:System.Windows.Forms.Control.MaximumSize%2A> et <xref:System.Windows.Forms.Control.MinimumSize%2A> d'un contrôle sont toujours honorées, indépendamment de la valeur de sa propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.|Les propriétés <xref:System.Windows.Forms.Control.MaximumSize%2A> et <xref:System.Windows.Forms.Control.MinimumSize%2A> ne sont pas affectées par la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.|  
|Il n'y a pas de taille minimale définie par défaut.|Cela signifie que si un contrôle est configuré pour être réduit sous <xref:System.Windows.Forms.Control.AutoSize%2A> et ne possède pas de contenu, la valeur de sa propriété <xref:System.Windows.Forms.Control.Size%2A> est 0,0.  Dans ce cas, votre contrôle sera réduit jusqu'à un certain point et ne sera pas aisément visible.|  
|Si un contrôle n'implémente pas la méthode <xref:System.Windows.Forms.Control.GetPreferredSize%2A>, la méthode <xref:System.Windows.Forms.Control.GetPreferredSize%2A> retourne la dernière valeur assignée à la propriété <xref:System.Windows.Forms.Control.Size%2A>.|Cela signifie que le fait d'attribuer à <xref:System.Windows.Forms.Control.AutoSize%2A> la valeur `true` n'aura aucun effet.|  
|Un contrôle dans une cellule <xref:System.Windows.Forms.TableLayoutPanel> réduit toujours sa taille pour tenir dans la cellule jusqu'à ce que sa <xref:System.Windows.Forms.Control.MinimumSize%2A> soit atteinte.|Cette taille est appliquée comme taille maximale.  Ce n'est pas le cas lorsque la cellule fait partie d'une ligne ou d'une colonne <xref:System.Windows.Forms.SizeType>.|  
  
## Propriété AutoSizeMode  
 La propriété `AutoSizeMode` permet un contrôle plus fin du comportement <xref:System.Windows.Forms.Control.AutoSize%2A> par défaut.  La propriété `AutoSizeMode` spécifie comment un contrôle se dimensionne lui\-même par rapport à son contenu.  Par exemple, le contenu pourrait être le texte pour un contrôle <xref:System.Windows.Forms.Button> ou les contrôles enfants pour un conteneur.  
  
 Le tableau suivant affiche les paramètres <xref:System.Windows.Forms.AutoSizeMode> et une description du comportement que chaque paramètre est fournie.  
  
|Paramètre AutoSizeMode|Comportement|  
|----------------------------|------------------|  
|GrowAndShrink|Le contrôle augmente ou réduit sa taille pour englober son contenu.<br /><br /> Les valeurs <xref:System.Windows.Forms.Control.MinimumSize%2A> et <xref:System.Windows.Forms.Control.MaximumSize%2A> sont honorées, mais la valeur actuelle de la propriété <xref:System.Windows.Forms.Control.Size%2A> est ignorée.<br /><br /> C'est le même comportement que les contrôles avec la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> et sans propriété `AutoSizeMode`.|  
|GrowOnly|Le contrôle augmente sa taille autant que nécessaire de façon à englober son contenu, mais ne la diminue pas à une valeur inférieure à celle spécifiée par sa propriété <xref:System.Windows.Forms.Control.Size%2A>.<br /><br /> C'est la valeur par défaut pour `AutoSizeMode`.|  
  
## Contrôles qui prennent en charge la propriété AutoSize  
 Le tableau suivant répertorie les contrôles qui prennent en charge les propriétés <xref:System.Windows.Forms.Control.AutoSize%2A> et `AutoSizeMode`.  
  
|Prise en charge de AutoSize|Type de contrôle|  
|---------------------------------|----------------------|  
|-   La propriété <xref:System.Windows.Forms.Control.AutoSize%2A> est prise en charge.<br />-   Pas de propriété `AutoSizeMode`.|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> \(<xref:System.Windows.Forms.TextBox> base\)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   La propriété <xref:System.Windows.Forms.Control.AutoSize%2A> est prise en charge.<br />-   La propriété `AutoSizeMode` est prise en charge.|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-   Pas de propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## Redimensionnement automatiquement dans l'environnement de design  
 Le tableau suivant décrit le comportement de dimensionnement d'un contrôle au moment du design, selon la valeur de ses propriétés <xref:System.Windows.Forms.Control.AutoSize%2A> et `AutoSizeMode`.  
  
 Substituez la propriété <xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> pour déterminer si un contrôle donné est dans un état redimensionnable par l'utilisateur.  Dans le tableau suivant, « ne peut pas » signifie <xref:System.Windows.Forms.Design.SelectionRules> uniquement, « peut » signifie <xref:System.Windows.Forms.Design.SelectionRules> et <xref:System.Windows.Forms.Design.SelectionRules>.  
  
|Paramètres AutoSize|Opération de dimensionnement au moment du design|  
|-------------------------|------------------------------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   Pas de propriété `AutoSizeMode`.|L'utilisateur ne peut pas redimensionner le contrôle au moment du design, à l'exception des contrôles suivants :<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   `AutoSizeMode` \= <xref:System.Windows.Forms.AutoSizeMode>|L'utilisateur ne peut pas redimensionner le contrôle au moment du design.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   `AutoSizeMode` \= <xref:System.Windows.Forms.AutoSizeMode>|L'utilisateur peut redimensionner le contrôle au moment du design.  Lorsque la propriété <xref:System.Windows.Forms.Control.Size%2A> est définie, l'utilisateur peut  uniquement augmenter la taille du contrôle.|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `false`, ou la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> est masquée.|L'utilisateur peut redimensionner le contrôle au moment du design.|  
  
> [!NOTE]
>  Pour maximaliser la productivité, le Concepteur Windows Forms masque la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> pour la classe <xref:System.Windows.Forms.Form>.  Au moment du design, le formulaire se comporte comme si la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> a la valeur `false`, indépendamment de son paramètre réel.  Au moment de l'exécution, aucun aménagement spécial n'est effectué, et la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> est appliquée comme spécifié par le paramètre de propriété.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.AutoSize%2A>   
 <xref:System.Windows.Forms.Control.PreferredSize%2A>   
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>