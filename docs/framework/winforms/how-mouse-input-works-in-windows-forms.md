---
title: "Fonctionnement des entr&#233;es de la souris dans les Windows Forms | Microsoft Docs"
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
  - "souris, entrée"
  - "Windows Forms, entrées de la souris"
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Fonctionnement des entr&#233;es de la souris dans les Windows Forms
La réception et la gestion des entrées de la souris constituent une part importante des applications Windows.  Vous pouvez gérer des événements de la souris pour exécuter une action dans votre application ou utiliser les informations sur l'emplacement de la souris pour exécuter des tests d'atteinte ou d'autres actions.  De plus, vous pouvez modifier la façon dont les contrôles de votre application gèrent les entrées de la souris.  Cette rubrique décrit ces événements de souris de façon détaillée et indique comment obtenir et modifier les paramètres système de la souris.  Pour plus d'informations sur les données fournies avec les événements de la souris et sur l'ordre dans lequel les événements de clic de souris sont déclenchés, consultez [Événements liés à la souris dans les Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## Emplacement de la souris et tests d'atteinte  
 Lorsque l'utilisateur déplace la souris, le système d'exploitation déplace le pointeur de la souris.  Le pointeur de la souris contient un seul pixel, appelé zone réactive, que le système d'exploitation suit et reconnaît comme étant la position du pointeur.  Lorsque l'utilisateur déplace la souris ou appuie sur un bouton de souris, le contrôle <xref:System.Windows.Forms.Control> qui contient <xref:System.Windows.Forms.Cursor.HotSpot%2A> déclenche l'événement de souris approprié.  Vous pouvez obtenir la position actuelle de la souris avec la propriété <xref:System.Windows.Forms.MouseEventArgs.Location%2A> de <xref:System.Windows.Forms.MouseEventArgs> lors de la gestion d'un événement de souris ou de l'utilisation de la propriété <xref:System.Windows.Forms.Cursor.Position%2A> de la classe <xref:System.Windows.Forms.Cursor>.  Vous pouvez utiliser par la suite les informations sur l'emplacement de la souris pour exécuter des tests d'atteinte, puis exécuter une action basée sur l'emplacement de la souris.  La fonction de tests d'atteinte est présente dans plusieurs contrôles au sein de Windows Forms \(tels que les contrôles <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> et <xref:System.Windows.Forms.DataGridView>\).  Utilisés avec l'événement de souris approprié \(<xref:System.Windows.Forms.Control.MouseHover>, par exemple\), les tests d'atteinte sont très utiles pour déterminer à quel moment votre application doit exécuter une action spécifique.  
  
## Événements de souris  
 Le principal moyen de répondre aux entrées de souris consiste à gérer des événements de souris.  Le tableau suivant affiche les événements de souris et décrit le moment où ils sont déclenchés.  
  
|Événement de souris|Description|  
|-------------------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Cet événement se produit lorsque vous relâchez le bouton de souris \(en général avant l'événement <xref:System.Windows.Forms.Control.MouseUp>\).  Le gestionnaire de cet événement reçoit un argument de type <xref:System.EventArgs>.  Utilisez cet événement lorsque vous devez seulement déterminer à quel moment un clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Cet événement se produit lorsque l'utilisateur clique sur le contrôle avec la souris.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.  Utilisez cet événement lorsque vous devez obtenir des informations à propos de la souris au moment d'un clic.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Cet événement se produit lorsque vous double\-cliquez sur le contrôle.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.EventArgs>.  Utilisez cet événement lorsque vous devez seulement déterminer à quel moment un double\-clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Cet événement se produit lorsque l'utilisateur double\-clique sur le contrôle avec la souris.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.  Utilisez cet événement lorsque vous devez obtenir des informations à propos de la souris au moment d'un double\-clic.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Cet événement se produit lorsque le pointeur de la souris se trouve sur le contrôle et que l'utilisateur appuie sur un bouton de souris.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Cet événement se produit lorsque le pointeur de la souris entre dans la bordure ou dans la zone cliente du contrôle, selon le type de contrôle concerné.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Cet événement se produit lorsque le pointeur de la souris s'arrête et reste sur le contrôle.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Cet événement se produit lorsque le pointeur de la souris quitte la bordure ou la zone cliente du contrôle, selon le type de contrôle concerné.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Cet événement se produit lorsque le pointeur de la souris se déplace pendant qu'il se trouve sur un contrôle.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Cet événement se produit lorsque le pointeur de la souris se trouve sur le contrôle et que l'utilisateur relâche un bouton de souris.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Cet événement se produit lorsque l'utilisateur fait pivoter la roulette de la souris pendant que le contrôle a le focus.  Le gestionnaire de cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.  Vous pouvez utiliser la propriété <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> de <xref:System.Windows.Forms.MouseEventArgs> pour déterminer la distance de défilement de la souris.|  
  
## Modification des entrées de la souris et détection des paramètres système  
 Vous pouvez détecter et modifier la façon dont un contrôle gère les entrées de la souris en dérivant du contrôle et en utilisant les méthodes <xref:System.Windows.Forms.Control.GetStyle%2A> et <xref:System.Windows.Forms.Control.SetStyle%2A>.  La méthode <xref:System.Windows.Forms.Control.SetStyle%2A> utilise une combinaison d'opérations de bits de valeurs <xref:System.Windows.Forms.ControlStyles> pour déterminer si le contrôle aura un comportement de clic standard ou de double\-clic, ou encore si le contrôle gérera son propre traitement de souris.  De plus, la classe <xref:System.Windows.Forms.SystemInformation> inclut des propriétés qui décrivent les fonctions de la souris et spécifient la façon dont la souris interagit avec le système d'exploitation.  Le tableau suivant récapitule ces propriétés.  
  
|Propriété|Description|  
|---------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Permet d'obtenir les dimensions \(exprimées en pixels\) de la zone dans laquelle l'utilisateur doit cliquer deux fois pour que le système d'exploitation considère les deux clics comme un double\-clic.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Permet d'obtenir le nombre maximal de millisecondes qui peuvent s'écouler entre un premier clic et un deuxième clic pour que le système d'exploitation considère l'action de la souris comme un double\-clic.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Permet d'obtenir le nombre de boutons figurant sur la souris.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Permet d'obtenir une valeur qui indique si les fonctions des boutons gauche et droit de la souris ont été permutées.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Permet d'obtenir les dimensions, en pixels, du rectangle dans lequel le pointeur de la souris doit rester pendant le délai de pointage de la souris avant qu'un message de pointage de la souris ne soit généré.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Obtient le temps, en millisecondes, pendant lequel le pointeur doit rester dans le rectangle de planification avant qu'un message ne soit généré.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Permet d'obtenir une valeur indiquant si une souris est installée.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Permet d'obtenir une valeur indiquant la vitesse actuelle de la souris \(valeur comprise entre 1 et 20\).|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Permet d'obtenir une valeur indiquant si une souris avec roulette est installée.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Permet d'obtenir le montant de la valeur delta de l'incrément d'une rotation de roulette de souris.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Permet d'obtenir le nombre de lignes à faire défiler lorsque la roulette de la souris pivote.|  
  
## Voir aussi  
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)   
 [Capture de la souris dans les Windows Forms](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)   
 [Pointeurs de souris dans les Windows Forms](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)