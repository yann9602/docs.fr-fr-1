---
title: "Fonctionnement des entrées de la souris dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 20de05b5df3737ccc525cb50c81b51bcba766287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-mouse-input-works-in-windows-forms"></a>Fonctionnement des entrées de la souris dans les Windows Forms
Recevoir et traiter l’entrée de la souris sont une partie importante de toutes les applications Windows. Vous pouvez gérer les événements de souris pour effectuer une action dans votre application, ou utiliser les informations d’emplacement de la souris pour effectuer un test de positionnement ou d’autres actions. En outre, vous pouvez modifier la manière dont les contrôles de votre application gèrent les entrées de la souris. Cette rubrique décrit ces événements de souris en détail, et comment obtenir et modifier les paramètres de système de la souris. Pour plus d’informations sur les données fournies avec la souris sont déclenchés les événements et l’ordre dans lequel les événements de clic de souris, consultez [les événements de souris dans les Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## <a name="mouse-location-and-hit-testing"></a>Emplacement de la souris et le test de positionnement  
 Lorsque l’utilisateur déplace la souris, le système d’exploitation déplace le pointeur de la souris. Le pointeur de souris contient un seul pixel, appelé la zone réactive, qui le système d’exploitation suit et reconnaît que la position du pointeur. Lorsque l’utilisateur déplace la souris ou appuie sur un bouton de la souris, le <xref:System.Windows.Forms.Control> qui contient le <xref:System.Windows.Forms.Cursor.HotSpot%2A> déclenche l’événement de souris approprié. Vous pouvez obtenir la position actuelle de la souris avec le <xref:System.Windows.Forms.MouseEventArgs.Location%2A> propriété de la <xref:System.Windows.Forms.MouseEventArgs> lors du traitement d’un événement de souris ou à l’aide de la <xref:System.Windows.Forms.Cursor.Position%2A> propriété de la <xref:System.Windows.Forms.Cursor> classe. Vous pouvez ensuite utiliser les informations d’emplacement de la souris pour effectuer le test de positionnement et puis effectuez une action basée sur l’emplacement de la souris. Fonctionnalité de test de positionnement est intégrée à plusieurs contrôles dans les Windows Forms tels que les <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.MonthCalendar> et <xref:System.Windows.Forms.DataGridView> contrôles. Utilisée avec l’événement de souris approprié, <xref:System.Windows.Forms.Control.MouseHover> par exemple, le test de positionnement est très utile pour déterminer quand votre application doit effectuer une action spécifique.  
  
## <a name="mouse-events"></a>Événements de souris  
 Pour répondre à l’entrée de la souris, la principale consiste à gérer les événements de souris. Le tableau suivant présente les événements de la souris et décrit quand ils sont déclenchés.  
  
|Événement de souris|Description|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|Cet événement se produit lorsque le bouton de la souris est relâché, généralement avant le <xref:System.Windows.Forms.Control.MouseUp> événement. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>. Gérez cet événement lorsque vous devez seulement déterminer quand un clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseClick>|Cet événement se produit lorsque l’utilisateur clique sur le contrôle avec la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>. Gérez cet événement lorsque vous avez besoin pour obtenir des informations sur la souris lorsqu’un clic se produit.|  
|<xref:System.Windows.Forms.Control.DoubleClick>|Cet événement se produit lorsque l’utilisateur double-clique sur le contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>. Gérez cet événement lorsque vous devez seulement déterminer quand un double-clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|Cet événement se produit lorsque l’utilisateur double-clique sur le contrôle avec la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>. Gérez cet événement lorsque vous avez besoin pour obtenir des informations sur la souris lorsqu’un double-clic se produit.|  
|<xref:System.Windows.Forms.Control.MouseDown>|Cet événement se produit lorsque le pointeur de la souris se trouve sur le contrôle et l’utilisateur appuie sur le bouton de la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseEnter>|Cet événement se produit lorsque le pointeur de la souris entre dans la bordure ou la zone cliente du contrôle, selon le type de contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseHover>|Cet événement se produit lorsque le pointeur de la souris s’arrête et reste sur le contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseLeave>|Cet événement se produit lorsque le pointeur de la souris quitte la bordure ou la zone cliente du contrôle, en fonction du type du contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.EventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseMove>|Cet événement se produit lorsque le pointeur de la souris se déplace alors qu’il est sur un contrôle. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseUp>|Cet événement se produit lorsque le pointeur de la souris se trouve sur le contrôle et l’utilisateur relâche un bouton de la souris. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>.|  
|<xref:System.Windows.Forms.Control.MouseWheel>|Cet événement se produit lorsque l’utilisateur fait tourner la roulette de la souris alors que le contrôle a le focus. Le gestionnaire pour cet événement reçoit un argument de type <xref:System.Windows.Forms.MouseEventArgs>. Vous pouvez utiliser la <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> propriété du <xref:System.Windows.Forms.MouseEventArgs> pour déterminer la distance de défilement de la souris.|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>Modifier l’entrée de la souris et détection des paramètres système  
 Vous pouvez détecter et modifier la façon dont un contrôle gère l’entrée de la souris en dérivant du contrôle et en utilisant le <xref:System.Windows.Forms.Control.GetStyle%2A> et <xref:System.Windows.Forms.Control.SetStyle%2A> méthodes. Le <xref:System.Windows.Forms.Control.SetStyle%2A> méthode utilise une combinaison d’opérations de <xref:System.Windows.Forms.ControlStyles> valeurs afin de déterminer si le contrôle possédera standard cliquez ou double-cliquez sur le comportement ou si le contrôle gère son propre traitement de la souris. En outre, la <xref:System.Windows.Forms.SystemInformation> classe inclut des propriétés qui décrivent les fonctionnalités de la souris et de spécifient la façon dont la souris interagit avec le système d’exploitation. Le tableau suivant récapitule ces propriétés.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|Obtient les dimensions en pixels, de la zone dans laquelle l’utilisateur doit cliquer deux fois pour le système d’exploitation considère deux clics comme un double-clic.|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|Obtient le nombre maximal de millisecondes qui peuvent s’écouler entre un premier clic et un deuxième clic pour que le système d’exploitation considère l’action de la souris un double-clic.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|Obtient le nombre de boutons de la souris.|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|Obtient une valeur qui indique si les fonctions des boutons gauche et droit de la souris ont été permutées.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|Obtient les dimensions en pixels du rectangle dans lequel le pointeur de la souris doit rester pendant le délai de pointage de la souris avant qu'un message de pointage soit généré.|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|Obtient le temps en millisecondes pendant lequel le pointeur doit rester dans le rectangle sélectionné automatiquement par pointage avec la souris avant qu'un message de pointage soit généré.|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|Obtient une valeur indiquant si une souris est installée.|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|Obtient une valeur qui indique la vitesse actuelle de la souris, de 1 à 20.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|Obtient une valeur indiquant si une souris avec roulette est installée.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|Obtient la quantité de la valeur delta de l’incrément d’une rotation de roulette de souris unique.|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|Obtient le nombre de lignes à faire défiler lors de la rotation de la roulette de la souris.|  
  
## <a name="see-also"></a>Voir aussi  
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Capture de la souris dans les Windows Forms](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)  
 [Pointeurs de souris dans les Windows Forms](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)
