---
title: Partage de boucles de messages entre Win32 et WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dcf8baa87038bc5625d46968b39d759daae25cbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Partage de boucles de messages entre Win32 et WPF
Cette rubrique décrit comment implémenter une boucle de messages pour l’interopérabilité avec [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], à l’aide d’existant message exposition de boucle dans <xref:System.Windows.Threading.Dispatcher> ou en créant une boucle de messages distincte sur la [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] de votre code d’interopérabilité.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher et la boucle de messages  
 Un scénario normal pour l’interopérabilité et le clavier pris en charge consiste à implémenter <xref:System.Windows.Interop.IKeyboardInputSink>, ou à sous-classer à partir de classes qui implémentent déjà <xref:System.Windows.Interop.IKeyboardInputSink>, tel que <xref:System.Windows.Interop.HwndSource> ou <xref:System.Windows.Interop.HwndHost>. Toutefois, la prise en charge du récepteur de clavier ne traite pas tous les besoins de boucle de message possibles que peut-être envoyer et recevoir des messages entre les limites d’interopérabilité. Pour aider à formaliser une architecture de boucle de message application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit le <xref:System.Windows.Interop.ComponentDispatcher> (classe), qui définit un protocole simple pour une boucle de message à suivre.  
  
 <xref:System.Windows.Interop.ComponentDispatcher>est une classe statique qui expose plusieurs membres. La portée de chaque méthode est implicitement liée au thread appelant. Une boucle de messages doit appeler certaines de ces [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] à des moments critiques (comme défini dans la section suivante).  
  
 <xref:System.Windows.Interop.ComponentDispatcher>Fournit des événements que d’autres composants (par exemple, le récepteur de clavier) peuvent écouter. Le <xref:System.Windows.Threading.Dispatcher> appelle tous les contrôles de la classe <xref:System.Windows.Interop.ComponentDispatcher> méthodes dans une séquence appropriée. Si vous implémentez votre propre boucle de messages, votre code est chargé d’appeler <xref:System.Windows.Interop.ComponentDispatcher> méthodes de la même manière.  
  
 Appel de <xref:System.Windows.Interop.ComponentDispatcher> méthodes sur un thread n’appellera que les gestionnaires d’événements qui ont été enregistrés sur ce thread.  
  
## <a name="writing-message-loops"></a>Boucles de messages de l’écriture  
 Voici une liste de vérification de <xref:System.Windows.Interop.ComponentDispatcher> membres que vous utiliserez si vous écrivez votre propre boucle de messages :  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: votre boucle de messages doit appeler pour indiquer que le thread est modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: votre boucle de messages doit appeler pour indiquer que le thread a été rétabli à l’état non modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: votre boucle de messages doit appeler pour indiquer que <xref:System.Windows.Interop.ComponentDispatcher> doit déclencher le <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> événement. <xref:System.Windows.Interop.ComponentDispatcher>ne génère pas de <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> si <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> est `true`, mais les boucles de messages peuvent choisir d’appeler <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> même si <xref:System.Windows.Interop.ComponentDispatcher> ne peut pas y répondre en état modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: votre boucle de messages doit appeler pour indiquer qu’un nouveau message est disponible. La valeur de retour indique si un écouteur pour un <xref:System.Windows.Interop.ComponentDispatcher> événement géré le message. Si <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> retourne `true` (géré), le répartiteur ne doit rien faire davantage avec le message. Si la valeur de retour est `false`, le répartiteur est censé appeler le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fonction `TranslateMessage`, puis appelez `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Utilisation de ComponentDispatcher et gestion des messages existants  
 Voici une liste de vérification de <xref:System.Windows.Interop.ComponentDispatcher> membres que vous utiliserez si vous comptez sur les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] boucle de message.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: indique si l’application est passée modale (par exemple, une boucle de messages modale ont été envoyée). <xref:System.Windows.Interop.ComponentDispatcher>permet de suivre cet état, car la classe maintient un nombre de <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> et <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> appels à partir de la boucle de messages.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>et <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> événements suivent les règles standards pour les appels de délégués. Les délégués sont appelés dans un ordre non spécifié, et tous les délégués sont appelés même si le premier marque le message comme étant géré.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: indique un moment approprié et efficace pour le traitement inactivité (il n’existe pas d’autres messages en attente pour le thread). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>ne sera pas déclenchée si le thread est modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: déclenché pour tous les messages qui traite de la pompe de messages.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: déclenché pour tous les messages qui n’ont pas été gérés pendant <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Un message est considéré géré si après la <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> événement ou <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> événement, le `handled` paramètre passé par référence dans les données d’événement est `true`. Gestionnaires d’événements doivent ignorer le message si `handled` est `true`, car cela signifie que le gestionnaire différent géré le message en premier. Gestionnaires d’événements pour les deux événements peuvent modifier le message. Le répartiteur doit distribuer le message modifié et non le message inchangé d’origine. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>est remis à tous les écouteurs, mais l’intention architecturale est que seule la fenêtre de niveau supérieur contenant le HWND à laquelle les messages destinés doivent appeler le code en réponse au message.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Comment HwndSource traite des événements ComponentDispatcher  
 Si le <xref:System.Windows.Interop.HwndSource> est une fenêtre de niveau supérieur (pas de HWND parent), il sera enregistré avec <xref:System.Windows.Interop.ComponentDispatcher>. Si <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> est déclenché, et si le message est destiné le <xref:System.Windows.Interop.HwndSource> ou fenêtres enfants, <xref:System.Windows.Interop.HwndSource> appelle son <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> séquence de récepteur de clavier.  
  
 Si le <xref:System.Windows.Interop.HwndSource> n’est pas une fenêtre de niveau supérieur (possède un HWND parent), il n’y aura aucune gestion. Seule la fenêtre de niveau supérieur est attendue pour effectuer la gestion et il est censé être une fenêtre de niveau supérieur avec prise en charge du récepteur de clavier dans le cadre d’un scénario d’interopérabilité.  
  
 Si <xref:System.Windows.Interop.HwndHost.WndProc%2A> sur une <xref:System.Windows.Interop.HwndSource> est appelée sans une méthode de récepteur de clavier appropriés qui est appelée en premier, votre application reçoit les événements du clavier du niveau supérieur tels que <xref:System.Windows.UIElement.KeyDown>. Toutefois, aucune méthode de récepteur de clavier n’est appelé, ce qui permet de contourner des fonctionnalités du modèle d’entrée clavier souhaitables comme clé prise en charge de l’accès. Cela peut se produire si la boucle de message n’a pas notifié correctement le thread pertinent sur le <xref:System.Windows.Interop.ComponentDispatcher>, ou parce que le parent HWND n’a pas appelé les réponses de récepteur de clavier appropriée.  
  
 Un message atteint le récepteur de clavier ne peut pas être envoyé à HWND si vous avez ajouté des raccordements pour ce message à l’aide de la <xref:System.Windows.Interop.HwndSource.AddHook%2A> (méthode). Le message a été géré au niveau de pompe de message directement et non soumis à la `DispatchMessage` (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Interop.ComponentDispatcher>  
 <xref:System.Windows.Interop.IKeyboardInputSink>  
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Modèle de thread](../../../../docs/framework/wpf/advanced/threading-model.md)  
 [Vue d’ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)
