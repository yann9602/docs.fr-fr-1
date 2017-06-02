---
title: "Fonctionnement de l&#39;entr&#233;e au clavier | Microsoft Docs"
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
  - "entrée au clavier, à propos de l'entrée au clavier"
  - "claviers, entrée au clavier"
  - "Windows Forms, entrée au clavier"
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Fonctionnement de l&#39;entr&#233;e au clavier
Windows Forms traite les entrées au clavier en déclenchant des événements de clavier en réponse à des messages Windows.  La plupart des applications Windows Forms traitent exclusivement les entrées au clavier en gérant les événements de clavier.  Toutefois, vous devez comprendre comment les messages de clavier fonctionnent pour pouvoir implémenter des scénarios d'entrée au clavier plus avancés, comme intercepter des touches avant qu'elles n'atteignent un contrôle.  Cette rubrique décrit les types de données clés que Windows Forms reconnaît et présente le routage des messages de clavier.  Pour plus d'informations sur les événements de clavier, consultez [Utilisation des événements du clavier](../../../docs/framework/winforms/using-keyboard-events.md).  
  
## Types de touches  
 Windows Forms identifie les entrées au clavier comme des codes de touche virtuels qui sont représentés par l'énumération <xref:System.Windows.Forms.Keys> de bits.  Avec l'énumération <xref:System.Windows.Forms.Keys>, vous pouvez combiner une série de touches enfoncées pour produire une valeur unique.  Ces valeurs correspondent aux valeurs qui accompagnent les messages Windows WM\_KEYDOWN et WM\_SYSKEYDOWN.  Vous pouvez détecter la plupart des enfoncements de touche physiques à l'aide des événements <xref:System.Windows.Forms.Control.KeyDown> ou <xref:System.Windows.Forms.Control.KeyUp>.  Les touches de caractère sont un sous\-ensemble de l'énumération <xref:System.Windows.Forms.Keys> et correspondent aux valeurs qui accompagnent les messages Windows WM\_CHAR et WM\_SYSCHAR.  Si la combinaison de touches enfoncées produit un caractère, vous pouvez détecter le caractère en gérant l'événement <xref:System.Windows.Forms.Control.KeyPress>.  Vous pouvez également utiliser <xref:Microsoft.VisualBasic.Devices.Keyboard>, exposé par l'interface de programmation Visual Basic, pour découvrir quelles touches ont été enfoncées et envoyer les touches.  Pour plus d'informations, consultez [Accessing the Keyboard](../Topic/Accessing%20the%20Keyboard%20\(Visual%20Basic\).md).  
  
## Ordre des événements de clavier  
 Comme précédemment répertorié, trois événements de clavier apparentés peuvent se produire sur un contrôle.  La séquence suivante affiche l'ordre général des événements :  
  
1.  L'utilisateur enfonce la touche "a", la touche est prétraitée, distribuée et un événement <xref:System.Windows.Forms.Control.KeyDown> se produit.  
  
2.  L'utilisateur maintient la touche "a" enfoncée, la touche est prétraitée, distribuée et un événement <xref:System.Windows.Forms.Control.KeyPress> se produit.  
  
     Cet événement se produit plusieurs fois, tant que l'utilisateur maintient une touche enfoncée.  
  
3.  L'utilisateur relâche la touche "a", la touche est prétraitée, distribuée et un événement <xref:System.Windows.Forms.Control.KeyUp> se produit.  
  
## Prétraitement des touches  
 Comme d'autres messages, les messages de clavier sont traités dans la méthode <xref:System.Windows.Forms.Control.WndProc%2A> d'un formulaire ou d'un contrôle.  Toutefois, avant que les messages de clavier soient traités, la méthode <xref:System.Windows.Forms.Control.PreProcessMessage%2A> appelle une ou plusieurs méthodes qui peuvent être substituées pour gérer des touches de caractère spécial et des touches physiques.  Vous pouvez substituer ces méthodes pour détecter et filtrer certaines touches avant que les messages soient traités par le contrôle.  Le tableau suivant montre l'action qui est exécutée et la méthode associée qui se produit, dans l'ordre dans lequel a lieu la méthode.  
  
### Prétraitement d'un événement KeyDown  
  
|Action|Méthode connexe|Remarques|  
|------------|---------------------|---------------|  
|Recherchez une touche de commande comme un accélérateur ou un raccourci de menu.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Cette méthode traite une touche de commande, qui a priorité sur les touches normales.  Si cette méthode retourne `true`, le message de la touche n'est pas distribué et un événement de touche ne se produit pas.  S'il retourne `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> est appelé `.`|  
|Recherchez une touche spéciale nécessitant un prétraitement ou un caractère normal qui doit déclencher un événement <xref:System.Windows.Forms.Control.KeyDown> et être distribué vers un contrôle.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Si la méthode retourne `true`, cela signifie que le contrôle est un caractère normal et un événement <xref:System.Windows.Forms.Control.KeyDown> est déclenché.  Si la méthode retourne `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> est appelé. **Note:**  Pour veiller à ce qu'un contrôle obtienne une touche ou une combinaison de touches, vous pouvez gérer l'événement <xref:System.Windows.Forms.Control.PreviewKeyDown> et donner la valeur `true` à <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> du <xref:System.Windows.Forms.PreviewKeyDownEventArgs> pour la ou les touches que vous souhaitez.|  
|Recherchez une touche de navigation \(échap, TAB, Retour ou les touches de direction\).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Cette méthode traite une touche physique qui emploie une fonctionnalité spéciale dans le contrôle, comme alterner le focus entre le contrôle et son parent.  Si le contrôle immédiat ne gère pas la touche, le <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> est appelé le contrôle parent et ainsi de suite jusqu'au contrôle le plus élevé dans la hiérarchie.  Si cette méthode retourne `true`, le prétraitement est terminé et un événement de touche n'est pas généré.  Si elle retourne `false`, un événement <xref:System.Windows.Forms.Control.KeyDown> se produit.|  
  
### Prétraitement d'un événement KeyPress  
  
|Action|Méthode connexe|Remarques|  
|------------|---------------------|---------------|  
|Vérifiez si la touche est un caractère normal devant être traité par le contrôle|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Si le caractère est un caractère normal, cette méthode retourne `true`, l'événement <xref:System.Windows.Forms.Control.KeyPress> est déclenché et plus aucune tâche de prétraitement ne se produit.  Sinon, <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> sera appelé.|  
|Vérifiez si le caractère est un mnémonique \(tel que &OK sur un bouton\)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Cette méthode, semblable à <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, sera appelée sur la hiérarchie de contrôle.  Si le contrôle est un contrôle conteneur, il recherche les mnémoniques en appelant <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> sur lui\-même et ses contrôles enfants.  Si <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> retourne `true`, un événement <xref:System.Windows.Forms.Control.KeyPress> ne se produit pas.|  
  
## Traitement de messages de clavier  
 Lorsque les messages de clavier atteignent la méthode <xref:System.Windows.Forms.Control.WndProc%2A> d'un formulaire ou d'un contrôle, ils sont traités par un jeu de méthodes qui peuvent être substituées.  Chacune de ces méthodes retourne une valeur <xref:System.Boolean> qui spécifie si le message de clavier a été traité et consommé par le contrôle.  Si l'une des méthodes retourne `true`, le message est considéré comme géré, et n'est pas passé à la base ou au parent du contrôle pour traitement ultérieur.  Sinon, le message reste dans la file d'attente et peut être traité dans une autre méthode dans la base ou le parent du contrôle.  Le tableau suivant présente les méthodes qui traitent des messages de clavier.  
  
|Méthode|Remarques|  
|-------------|---------------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Cette méthode traite tous les messages de clavier qui sont reçus par la méthode <xref:System.Windows.Forms.Control.WndProc%2A> du contrôle.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Cette méthode envoie le message de clavier au parent du contrôle.  Si <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> retourne `true`, aucun événement de touche n'est généré, sinon <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> est appelé.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Cette méthode déclenche les événements <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress> et <xref:System.Windows.Forms.Control.KeyUp>, selon les circonstances.|  
  
## Substitution des méthodes de clavier  
 Il existe de nombreuses méthodes pouvant être substituées pendant le prétraitement et le traitement d'un message de clavier. Toutefois, certaines méthodes constituent de meilleurs choix que d'autres.  Le tableau suivant présente les tâches que vous pouvez souhaiter accomplir et la meilleure manière de substituer les méthodes de clavier.  Pour plus d'informations sur la substitution de méthodes, consultez [NOT IN BUILD: Overriding Properties and Methods](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
|Tâche|Méthode|  
|-----------|-------------|  
|Intercepter une touche de navigation et déclencher un événement <xref:System.Windows.Forms.Control.KeyDown>.  Par exemple, vous souhaitez que TAB et Retour soient gérées dans une zone de texte.|Override <xref:System.Windows.Forms.Control.IsInputKey%2A>. **Note:**  Vous pouvez également gérer l'événement <xref:System.Windows.Forms.Control.PreviewKeyDown> et définir <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> de <xref:System.Windows.Forms.PreviewKeyDownEventArgs> sur `true` pour la ou les touches que vous souhaitez.|  
|Gérer une entrée ou une navigation spéciale sur un contrôle.  Par exemple, vous souhaitez l'utilisation de touches de direction dans votre contrôle List pour modifier l'élément sélectionné.|Override <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>.|  
|Intercepter une touche de navigation et déclencher un événement <xref:System.Windows.Forms.Control.KeyPress>.  Par exemple dans un contrôle de zone de sélection numérique, vous souhaitez qu'une touche de direction soit enfoncée plusieurs fois pour accélérer la progression à travers les éléments.|Override <xref:System.Windows.Forms.Control.IsInputChar%2A>.|  
|Gérer une entrée ou une navigation spéciale sur un contrôle pendant un événement <xref:System.Windows.Forms.Control.KeyPress>.  Par exemple, dans un contrôle List, maintenir enfoncée la touche "r" permet de passer d'un élément commençant par la lettre r au suivant.|Override <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>.|  
|Exécuter une gestion personnalisée des mnémoniques ; par exemple, vous souhaitez gérer les mnémoniques sur des boutons owner\-drawn contenus dans une barre d'outils.|Override <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.Keys>   
 <xref:System.Windows.Forms.Control.WndProc%2A>   
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>   
 [My.Computer.Keyboard Object](../../../ocs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)   
 [Accessing the Keyboard](../Topic/Accessing%20the%20Keyboard%20\(Visual%20Basic\).md)   
 [Utilisation des événements du clavier](../../../docs/framework/winforms/using-keyboard-events.md)