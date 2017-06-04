---
title: "Partage de boucles de messages entre Win32 et WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interopérabilité (WPF), Win32"
  - "boucles de message (WPF)"
  - "partager des boucles de messages"
  - "code Win32, partager des boucles de messages"
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Partage de boucles de messages entre Win32 et WPF
Cette rubrique décrit comment implémenter une boucle de messages pour l'interopérabilité avec [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], en utilisant l'exposition de boucle de messages existante dans <xref:System.Windows.Threading.Dispatcher> ou en créant une boucle de messages séparée du côté [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] de votre code d'interopérabilité.  
  
## ComponentDispatcher et la boucle de messages  
 Un scénario normal pour l'interopérabilité et la prise en charge d'événement clavier consiste à implémenter <xref:System.Windows.Interop.IKeyboardInputSink> ou à sous\-classer à partir de classes qui implémentent déjà <xref:System.Windows.Interop.IKeyboardInputSink>, telles que <xref:System.Windows.Interop.HwndSource> ou <xref:System.Windows.Interop.HwndHost>.  Toutefois, la prise en charge du récepteur du clavier ne traite pas tous les besoins de la boucle de messages que vous pouvez rencontrer lors de l'envoi et de la réception de messages à travers vos limites d'interopérabilité.  Afin d'aider à formaliser une architecture de boucle de messages d'application, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit la classe <xref:System.Windows.Interop.ComponentDispatcher>, qui définit un protocole simple pour une boucle de messages à suivre.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> est une classe statique qui expose plusieurs membres.  La portée de chaque méthode est liée implicitement au thread appelant.  Une boucle de messages doit appeler certaines de ces [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] à des moments critiques \(comme défini dans la section suivante\).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> fournit des événements que d'autres composants \(tel que le récepteur de clavier\) peuvent écouter.  La classe <xref:System.Windows.Threading.Dispatcher> appelle toutes les méthodes <xref:System.Windows.Interop.ComponentDispatcher> appropriées dans une séquence appropriée.  Si vous implémentez votre propre boucle de messages, votre code est chargé d'appeler des méthodes <xref:System.Windows.Interop.ComponentDispatcher> de façon similaire.  
  
 L'appel de méthodes <xref:System.Windows.Interop.ComponentDispatcher> sur un thread n'appellera que les gestionnaires d'événements enregistrés sur ce thread.  
  
## Écriture de boucles de messages  
 Les éléments suivants sont une liste de contrôle des membres <xref:System.Windows.Interop.ComponentDispatcher> que vous utiliserez si vous écrivez votre propre boucle de messages :  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> : Méthode que votre boucle de messages doit appeler pour indiquer que le thread est modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> : Méthode que votre boucle de messages doit appeler pour indiquer que le thread a été rétabli à l'état non modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> : votre boucle de messages doit appeler cette méthode pour indiquer que <xref:System.Windows.Interop.ComponentDispatcher> doit déclencher l'événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>.  <xref:System.Windows.Interop.ComponentDispatcher> ne déclenchera pas <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> si <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> a la valeur `true`, mais les boucles de messages peuvent choisir d'appeler <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> même si <xref:System.Windows.Interop.ComponentDispatcher> ne peut pas lui répondre en état modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> : Méthode que votre boucle de messages doit appeler pour indiquer qu'un nouveau message est disponible.  La valeur de retour indique si un écouteur d'événement <xref:System.Windows.Interop.ComponentDispatcher> a géré le message.  Si <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> retourne la valeur `true` \(géré\), le répartiteur en a fini avec le message.  Si la valeur de retour est `false`, le répartiteur est supposé appeler la fonction [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]`TranslateMessage`, puis appeler `DispatchMessage`.  
  
## Utilisation de ComponentDispatcher et gestion des messages existants  
 Les éléments suivants sont une liste de contrôle des membres <xref:System.Windows.Interop.ComponentDispatcher> que vous utiliserez si vous utilisez la boucle de messages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inhérente.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> : indique si l'application est passée en mode modal \(par exemple, une boucle de messages modale a fait l'objet d'un push\).  <xref:System.Windows.Interop.ComponentDispatcher> peut effectuer le suivi de cet état car la classe tient le compte des appels <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> et <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> à partir de la boucle de messages.  
  
-   Les événements <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> et <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> suivent les règles standards pour les appels de délégué.  Les délégués sont appelés dans un ordre non spécifié et tous les délégués sont appelés même si le premier marque le message comme étant géré.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> : indique un moment approprié et efficace pour le traitement des temps d'inactivité \(il n'y a pas d'autres messages en attente pour le thread\).  <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> n'est pas déclenché si le thread est modal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> : déclenché pour tous les messages que la pompe de messages traite.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> : déclenché pour tous les messages qui n'ont pas été gérés pendant <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Un message est considéré géré si après l'événement <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> ou <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>, le paramètre `handled` passé par référence dans les données d'événement est `true`.  Les gestionnaires d'événements doivent ignorer le message si `handled` est `true`, parce que cela signifie que le gestionnaire différent a géré le message en premier.  Les gestionnaires d'événements des deux événements peuvent modifier le message.  Le répartiteur doit distribuer le message modifié plutôt que le message inchangé d'origine.  <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> est remis à tous les écouteurs, mais l'intention architecturale est que seule la fenêtre de niveau supérieur contenant le HWND ciblé par les messages doit appeler le code en réponse au message.  
  
## Comment HwndSource traite des événements ComponentDispatcher  
 Si le <xref:System.Windows.Interop.HwndSource> est une fenêtre de niveau supérieur \(pas de HWND parent\), il s'enregistrera avec <xref:System.Windows.Interop.ComponentDispatcher>.  Si <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> est déclenché et si le message est prévu pour les fenêtres <xref:System.Windows.Interop.HwndSource> ou enfants, <xref:System.Windows.Interop.HwndSource> appelle son <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, séquence du récepteur du clavier <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A>.  
  
 Si le <xref:System.Windows.Interop.HwndSource> n'est pas une fenêtre de niveau supérieur \(possède un HWND parent\), aucune gestion n'aura lieu.  Seule la fenêtre de niveau supérieur est supposée effectuer la gestion, et une fenêtre de niveau supérieur est censée exister avec prise en charge du récepteur du clavier dans le cadre de tout scénario d'interopérabilité.  
  
 Si <xref:System.Windows.Interop.HwndHost.WndProc%2A> sur un <xref:System.Windows.Interop.HwndSource> est appelé sans appel préalable d'une méthode appropriée du récepteur du clavier, votre application recevra les événements du clavier du niveau supérieur tels que <xref:System.Windows.UIElement.KeyDown>.  Toutefois, aucune méthode du récepteur du clavier ne sera appelée, qui contournerait des fonctionnalités de modèle d'entrée au clavier souhaitables comme la prise en charge des touches d'accès rapide.  Cela peut arriver parce que la boucle de messages n'a pas notifié correctement le thread pertinent sur le <xref:System.Windows.Interop.ComponentDispatcher>, ou parce que le parent HWND n'a pas appelé les bonnes réponses du récepteur du clavier.  
  
 Un message qui s'adresse au récepteur du clavier ne peut pas être envoyé à HWND si vous avez ajouté des points de raccordements pour ce message en utilisant la méthode <xref:System.Windows.Interop.HwndSource.AddHook%2A>.  Le message a pu être géré directement au niveau de la pompe de messages et ne pas avoir été soumis à la fonction `DispatchMessage`.  
  
## Voir aussi  
 <xref:System.Windows.Interop.ComponentDispatcher>   
 <xref:System.Windows.Interop.IKeyboardInputSink>   
 [Interopérabilité WPF et Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)   
 [Modèle de thread](../../../../docs/framework/wpf/advanced/threading-model.md)   
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)