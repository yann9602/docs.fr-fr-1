---
title: "Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement ContextMenuOpening | Microsoft Docs"
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
  - "ContextMenuOpening (événement)"
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: g&#233;rer l&#39;&#233;v&#233;nement ContextMenuOpening
Vous pouvez gérer l'événement <xref:System.Windows.FrameworkElement.ContextMenuOpening> dans une application pour ajuster un menu contextuel existant avant son affichage ou pour supprimer un menu qui se serait normalement affiché en affectant la valeur `true` à la propriété <xref:System.Windows.RoutedEventArgs.Handled%2A> dans les données d'événement.  L'affectation de la valeur `true` à la propriété <xref:System.Windows.RoutedEventArgs.Handled%2A> dans les données d'événement a généralement pour but de remplacer le menu par un objet <xref:System.Windows.Controls.ContextMenu> totalement nouveau, qui requiert parfois l'annulation de l'opération et le démarrage d'une nouvelle action d'ouverture.  Si vous écrivez des gestionnaires pour l'événement <xref:System.Windows.FrameworkElement.ContextMenuOpening>, gardez à l'esprit les problèmes de synchronisation entre un contrôle <xref:System.Windows.Controls.ContextMenu> et le service chargé d'ouvrir et de positionner les menus contextuels pour les contrôles en général.  Cette rubrique illustre quelques\-unes des techniques de codage pour différents scénarios d'ouverture de menus contextuels, ainsi qu'un cas où le problème de synchronisation se pose.  
  
 Il existe plusieurs scénarios pour gérer l'événement <xref:System.Windows.FrameworkElement.ContextMenuOpening> :  
  
-   Ajustement des éléments de menu avant l'affichage  
  
-   Remplacement de l'intégralité du menu avant l'affichage  
  
-   Suppression totale d'un menu contextuel existant pour ne rien afficher  
  
## Exemple  
  
## Ajustement des éléments de menu avant l'affichage  
 L'ajustement des éléments de menu existants est une opération relativement simple et est probablement le scénario le plus courant.  Vous pouvez ajuster des menus pour ajouter ou supprimer des options de menu contextuel en réponse aux informations d'état actuelles dans votre application ou à des informations d'état particulières disponibles sous forme de propriété sur l'objet pour lequel le menu contextuel est demandé.  
  
 La technique générale consiste à obtenir la source de l'événement, qui est le contrôle sur lequel vous avez cliqué avec le bouton droit, puis d'en obtenir la propriété <xref:System.Windows.FrameworkElement.ContextMenu%2A>.  En général, vous vérifierez la collection <xref:System.Windows.Controls.ItemsControl.Items%2A> afin de voir les éléments de menu contextuel qui existent déjà dans le menu, puis ajouterez ou supprimerez les éléments <xref:System.Windows.Controls.MenuItem> appropriés à ou depuis la collection.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## Remplacement de l'intégralité du menu avant l'affichage  
 Un autre scénario consiste à remplacer l'intégralité du menu contextuel.  Vous pouvez évidemment utiliser une variation du code précédent et supprimer chaque élément d'un menu contextuel existant avant d'en ajouter de nouveaux, en commençant par l'élément zéro.  Cependant, l'approche la plus intuitive pour remplacer tous les éléments du menu contextuel consiste à créer un <xref:System.Windows.Controls.ContextMenu>, à le remplir d'éléments, puis à définir la propriété <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName> d'un contrôle pour qu'elle soit le nouveau <xref:System.Windows.Controls.ContextMenu>.  
  
 L'exemple suivant présente le code de gestionnaire simple utilisé pour remplacer un <xref:System.Windows.Controls.ContextMenu>.  Le code référence une méthode `BuildMenu` personnalisée qui est séparée car elle est appelée par plusieurs des exemples de gestionnaires.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Si vous utilisez ce style de gestionnaire pour <xref:System.Windows.FrameworkElement.ContextMenuOpening>, vous risquez toutefois de créer un problème de synchronisation si l'objet dans lequel vous définissez le <xref:System.Windows.Controls.ContextMenu> ne possède pas de menu contextuel préexistant.  Lorsqu'un utilisateur clique avec le bouton droit sur un contrôle, <xref:System.Windows.FrameworkElement.ContextMenuOpening> est déclenché même si le <xref:System.Windows.Controls.ContextMenu> existant est vide ou null.  Dans ce cas, quel que soit le nouveau <xref:System.Windows.Controls.ContextMenu> que vous définissez sur l'élément source, il arrivera trop en retard pour être affiché.  Si l'utilisateur clique alors une deuxième fois avec le bouton droit, votre nouveau <xref:System.Windows.Controls.ContextMenu> apparaît, la valeur est non null et votre gestionnaire remplace et affiche correctement le menu lorsqu'il s'exécute pour la deuxième fois.  Cela laisse entendre qu'il existe deux solutions possibles :  
  
1.  Assurez\-vous que les gestionnaires <xref:System.Windows.FrameworkElement.ContextMenuOpening> s'exécutent toujours sur des contrôles qui ont au moins un espace réservé <xref:System.Windows.Controls.ContextMenu> disponible, que vous prévoyez de remplacer par le code du gestionnaire.  Dans ce cas, vous pouvez utiliser le gestionnaire présenté dans l'exemple précédent, mais en assignant un espace réservé <xref:System.Windows.Controls.ContextMenu> dans la balise initiale :  
  
     [!code-xml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  Imaginez que la valeur <xref:System.Windows.Controls.ContextMenu> initiale puisse être null, sur la base d'une logique provisoire.  Vous pouvez soit vérifier si le <xref:System.Windows.Controls.ContextMenu> contient une valeur null, soit utiliser un indicateur dans votre code pour vérifier si votre gestionnaire a été exécuté au moins une fois.  Comme vous supposez que le <xref:System.Windows.Controls.ContextMenu> est sur le point d'être affiché, votre gestionnaire affecte alors la valeur `true` à <xref:System.Windows.RoutedEventArgs.Handled%2A> dans les données d'événement.  Pour le <xref:System.Windows.Controls.ContextMenuService> responsable de l'affichage de menu contextuel, une valeur `true` pour <xref:System.Windows.RoutedEventArgs.Handled%2A> dans les données d'événement représente une demande d'annulation de l'affichage de la combinaison menu contextuel\/contrôle qui a déclenché l'événement.  
  
 Maintenant que vous avez supprimé le menu contextuel potentiellement suspect, l'étape suivante consiste à en définir un nouveau, puis à l'afficher.  La procédure de définition du nouveau menu est quasiment identique à celle du gestionnaire précédent : vous générez un nouveau <xref:System.Windows.Controls.ContextMenu> et définissez la propriété <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName> de la source de contrôle associée.  La seule nouveauté est que vous devez maintenant forcer l'affichage du menu contextuel, car vous avez supprimé la première tentative.  Pour ce faire, vous devez affecter la valeur `true` à la propriété <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=fullName> dans le gestionnaire.  Soyez prudent lors de cette opération, car l'ouverture du menu contextuel dans le gestionnaire déclenche à nouveau l'événement <xref:System.Windows.FrameworkElement.ContextMenuOpening>.  Si vous entrez à nouveau votre gestionnaire, il devient récurrent à l'infini.  C'est pourquoi vous devez toujours vérifier la présence d'une valeur `null` ou utiliser un indicateur si vous ouvrez un menu contextuel à partir d'un gestionnaire d'événements <xref:System.Windows.FrameworkElement.ContextMenuOpening>.  
  
## Suppression d'un menu contextuel existant pour ne rien afficher  
 Le dernier scénario, à savoir l'écriture d'un gestionnaire supprimant totalement un menu, est rare.  Si un contrôle donné n'est pas supposé afficher un menu contextuel, il existe probablement des mesures plus appropriées pour l'en empêcher que la suppression du menu à la demande d'un utilisateur.  Mais si vous souhaitez utiliser le gestionnaire pour supprimer un menu contextuel et ne rien afficher, votre gestionnaire doit simplement affecter la valeur `true` à <xref:System.Windows.RoutedEventArgs.Handled%2A> dans les données d'événement.  Le <xref:System.Windows.Controls.ContextMenuService> chargé d'afficher un menu contextuel vérifie les données de l'événement qu'il a déclenché sur le contrôle.  Si l'événement a été marqué <xref:System.Windows.RoutedEventArgs.Handled%2A> à un moment quelconque, l'action d'ouverture du menu contextuel initiée par l'événement est supprimée.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.ContextMenu>   
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=fullName>   
 [Vue d'ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [Vue d'ensemble de ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-overview.md)