---
title: "Fonctionnement de l'entrée au clavier"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f45d01da6f9a851a0e51f9d614e84a3fba91e4d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-keyboard-input-works"></a>Fonctionnement de l'entrée au clavier
Windows Forms traite l’entrée au clavier en déclenchant des événements de clavier en réponse aux messages de Windows. La plupart des applications Windows Forms traitent l’entrée au clavier exclusivement en gérant les événements de clavier. Toutefois, vous devez comprendre le fonctionnement des messages de clavier pour pouvoir implémenter des scénarios d’entrée au clavier plus avancés, comme l’interception des touches avant qu’elles n’atteignent un contrôle. Cette rubrique décrit les types de données de touches que Windows Forms reconnaît et fournit une vue d’ensemble du routage des messages de clavier. Pour plus d’informations sur les événements de clavier, consultez [Utilisation des événements de clavier](../../../docs/framework/winforms/using-keyboard-events.md).  
  
## <a name="types-of-keys"></a>Types de touches  
 Windows Forms identifie les entrées au clavier comme des codes de touche virtuelle qui sont représentées par l’opérateur de bits <xref:System.Windows.Forms.Keys> énumération. Avec la <xref:System.Windows.Forms.Keys> énumération, vous pouvez combiner une série de touches enfoncées pour produire une valeur unique. Ces valeurs correspondent aux valeurs qui accompagnent les messages Windows WM_KEYDOWN et WM_SYSKEYDOWN. Vous pouvez détecter les pressions plus physiques en gérant la <xref:System.Windows.Forms.Control.KeyDown> ou <xref:System.Windows.Forms.Control.KeyUp> événements. Touches de caractère sont un sous-ensemble de la <xref:System.Windows.Forms.Keys> énumération et correspondent aux valeurs qui accompagnent les messages Windows WM_CHAR et WM_SYSCHAR. Si la combinaison de touches enfoncées produit un caractère, vous pouvez détecter le caractère en gérant le <xref:System.Windows.Forms.Control.KeyPress> événement. Vous pouvez également utiliser <xref:Microsoft.VisualBasic.Devices.Keyboard>, exposé par l’interface de programmation Visual Basic, pour découvrir quelles touches ont été enfoncées et envoyer les touches. Pour plus d’informations, consultez [Accès au clavier](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md).  
  
## <a name="order-of-keyboard-events"></a>Ordre des événements de clavier  
 Comme indiqué précédemment, il existe 3 événements liés au clavier qui peuvent se produire sur un contrôle. La séquence suivante montre l’ordre général des événements :  
  
1.  L’utilisateur exécute un push de la touche « a », la clé est prétraitée, distribuée et un <xref:System.Windows.Forms.Control.KeyDown> événement se produit.  
  
2.  L’utilisateur maintient la touche « a », la clé est prétraitée, distribuée et un <xref:System.Windows.Forms.Control.KeyPress> événement se produit.  
  
     Cet événement se produit plusieurs fois lorsque l’utilisateur maintient une touche enfoncée.  
  
3.  L’utilisateur relâche la touche « a », la clé est prétraitée, distribués et un <xref:System.Windows.Forms.Control.KeyUp> événement se produit.  
  
## <a name="preprocessing-keys"></a>Prétraitement des touches  
 Comme d’autres messages, les messages de clavier sont traités dans le <xref:System.Windows.Forms.Control.WndProc%2A> méthode d’un formulaire ou un contrôle. Toutefois, avant de clavier les messages sont traités, le <xref:System.Windows.Forms.Control.PreProcessMessage%2A> méthode appelle une ou plusieurs méthodes qui peuvent être substituées pour gérer les touches de caractère spécial et des touches physiques. Vous pouvez substituer ces méthodes pour détecter et filtrer certaines touches avant que les messages ne soient traités par le contrôle. Le tableau suivant présente l’action exécutée et la méthode associée qui se produit, dans l’ordre où la méthode se produit.  
  
### <a name="preprocessing-for-a-keydown-event"></a>Prétraitement d’un événement KeyDown  
  
|Action|Méthode associée|Notes|  
|------------|--------------------|-----------|  
|Rechercher une touche de commande comme un accélérateur ou un raccourci du menu.|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|Cette méthode traite une touche de commande, qui est prioritaire par rapport aux touches ordinaires. Si cette méthode renvoie `true`, le message de la touche n’est pas distribué et aucun événement de touche ne se produit. Si elle retourne `false`, <xref:System.Windows.Forms.Control.IsInputKey%2A> est appelée`.`|  
|Recherchez une touche spéciale nécessitant un prétraitement ou une touche de caractère normal qui doit déclencher un <xref:System.Windows.Forms.Control.KeyDown> événement et être distribué à un contrôle.|<xref:System.Windows.Forms.Control.IsInputKey%2A>|Si la méthode retourne `true`, cela signifie que le contrôle est un caractère normal et un <xref:System.Windows.Forms.Control.KeyDown> événement est déclenché. Si `false`, <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> est appelée. **Remarque :** pour garantir un contrôle obtienne une clé ou une combinaison de clés, vous pouvez gérer le <xref:System.Windows.Forms.Control.PreviewKeyDown> événement et ensemble <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> de la <xref:System.Windows.Forms.PreviewKeyDownEventArgs> à `true` pour l’ou les touches que vous souhaitez.|  
|Rechercher une touche de navigation (touches ÉCHAP, de tabulation, de retour ou de direction).|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|Cette méthode traite une touche physique qui emploie une fonctionnalité spéciale dans le contrôle, comme basculer l’objectif entre le contrôle et son parent. Si le contrôle immédiat ne gère pas la clé, le <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> est appelée sur le contrôle parent et ainsi de suite à un contrôle le plus élevé dans la hiérarchie. Si cette méthode renvoie `true`, le prétraitement est terminé et un événement de touche n’est pas généré. Si elle retourne `false`, un <xref:System.Windows.Forms.Control.KeyDown> événement se produit.|  
  
### <a name="preprocessing-for-a-keypress-event"></a>Prétraitement d’un événement KeyPress  
  
|Action|Méthode associée|Notes|  
|------------|--------------------|-----------|  
|Vérifier si la touche est un caractère normal qui doit être traité par le contrôle|<xref:System.Windows.Forms.Control.IsInputChar%2A>|Si le caractère est un caractère normal, cette méthode retourne `true`, le <xref:System.Windows.Forms.Control.KeyPress> événement est déclenché et aucun autre prétraitement se produit. Dans le cas contraire <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> sera appelée.|  
|Vérifier si le caractère est un caractère mnémonique (comme &OK sur un bouton)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|Cette méthode, semblable à <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>, sera appelée sur la hiérarchie des contrôles. Si le contrôle est un contrôle conteneur, il recherche les mnémoniques en appelant <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> sur lui-même et ses contrôles enfants. Si <xref:System.Windows.Forms.Control.ProcessDialogChar%2A> retourne `true`, un <xref:System.Windows.Forms.Control.KeyPress> événement ne se produit pas.|  
  
## <a name="processing-keyboard-messages"></a>Traitement des messages de clavier  
 Une fois que les messages de clavier atteignent la <xref:System.Windows.Forms.Control.WndProc%2A> méthode d’un formulaire ou un contrôle, ils sont traités par un ensemble de méthodes qui peuvent être substituées. Chacune de ces méthodes retourne une <xref:System.Boolean> valeur qui spécifie si le message de clavier a été traité et consommé par le contrôle. Si l’une des méthodes renvoie `true`, alors le message est considéré comme traité et n’est pas transmis à la base ou au parent du contrôle pour un traitement ultérieur. Dans le cas contraire, le message reste dans la file d’attente des messages et peut être traité dans une autre méthode de la base ou du parent du contrôle. Le tableau suivant présente les méthodes qui traitent les messages de clavier.  
  
|Méthode|Remarques|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|Cette méthode traite tous les messages de clavier qui sont reçus par le <xref:System.Windows.Forms.Control.WndProc%2A> méthode du contrôle.|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|Cette méthode envoie le message de clavier au parent du contrôle. Si <xref:System.Windows.Forms.Control.ProcessKeyPreview%2A> retourne `true`, aucun événement de touche n’est généré, sinon <xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A> est appelée.|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|Cette méthode déclenche la <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, et <xref:System.Windows.Forms.Control.KeyUp> événements, comme il convient.|  
  
## <a name="overriding-keyboard-methods"></a>Substitution des méthodes de clavier  
 Il existe de nombreuses méthodes pouvant être substituées pendant le prétraitement et le traitement d’un message de clavier. Toutefois, certaines méthodes sont mieux adaptées que d’autres. Le tableau suivant présente des tâches que vous voulez peut-être accomplir et la meilleure façon de substituer les méthodes de clavier. Pour plus d’informations sur les méthodes de substitution, consultez [substitution de propriétés et méthodes dans les classes dérivées](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes).  
  
|Tâche|Méthode|  
|----------|------------|  
|Intercepter une touche de navigation et déclencher un <xref:System.Windows.Forms.Control.KeyDown> événement. Par exemple, vous souhaitez que la touche de tabulation et la touche de retour soient gérées dans une zone de texte.|Substituez <xref:System.Windows.Forms.Control.IsInputKey%2A> **Remarque :** vous pouvez également gérer les <xref:System.Windows.Forms.Control.PreviewKeyDown> événement et jeu <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A> de la <xref:System.Windows.Forms.PreviewKeyDownEventArgs> à `true` pour l’ou les touches que vous souhaitez.|  
|Effectuer une entrée spéciale ou une gestion de navigation sur un contrôle. Par exemple, vous souhaitez utiliser les touches de direction dans votre contrôle de liste pour modifier l’élément sélectionné.|Substituer la méthode <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|Intercepter une touche de navigation et déclencher un <xref:System.Windows.Forms.Control.KeyPress> événement. Par exemple, dans un contrôle de zone de sélection, vous voulez que des activations multiples de la touche de direction accélèrent la progression au sein des éléments.|Substituez <xref:System.Windows.Forms.Control.IsInputChar%2A>|  
|Effectuer une gestion spéciale d’entrée ou de navigation pendant un <xref:System.Windows.Forms.Control.KeyPress> événement. Par exemple, dans une liste de contrôle, le fait de maintenir la touche « r » enfoncée permet d’ignorer les éléments qui commencent par la lettre r.|Substituer la méthode <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|Effectuer une gestion personnalisée des caractères mnémoniques ; par exemple, vous souhaitez gérer les caractères mnémoniques sur des boutons owner-drawn contenus dans une barre d’outils.|Substituez <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.WndProc%2A>  
 <xref:System.Windows.Forms.Control.PreProcessMessage%2A>  
 [My.Computer.Keyboard (objet)](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)  
 [Accès au clavier](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)  
 [Utilisation des événements de clavier](../../../docs/framework/winforms/using-keyboard-events.md)
