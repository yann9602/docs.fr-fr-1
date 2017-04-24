---
title: "Vue d&#39;ensemble des annotations | Microsoft Docs"
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
  - "documents, annotations"
  - "surbrillances"
  - "pense-bête"
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Vue d&#39;ensemble des annotations
La rédaction de remarques ou de commentaires sur papier est une activité tellement banale que nous pensons qu'elle va de soi.  Ces remarques ou commentaires sont des "annotations" qui sont ajoutés dans un document pour signaler des informations ou mettre en évidence des éléments présentant un intérêt particulier afin de s'y référer ultérieurement.  Bien que la rédaction de remarques sur un document papier soit une tâche simple et banale, la possibilité d'ajouter des commentaires personnels dans des documents électroniques, lorsque cette fonctionnalité est disponible, est généralement très limitée.  
  
 Cette rubrique passe en revue plusieurs types d'annotations courants, en particulier les pense\-bêtes et les surbrillances, et explique en quoi [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] simplifie leur utilisation dans les applications via les contrôles d'affichage de document [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  Les contrôles d'affichage de document [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] qui prennent en charge les annotations comprennent <xref:System.Windows.Controls.FlowDocumentReader> et <xref:System.Windows.Controls.FlowDocumentScrollViewer>, ainsi que les contrôles dévirés de <xref:System.Windows.Controls.Primitives.DocumentViewerBase>, tels que <xref:System.Windows.Controls.DocumentViewer> et <xref:System.Windows.Controls.FlowDocumentPageViewer>.  
  
   
  
<a name="caf1_type_stickynotes"></a>   
## Pense\-bêtes  
 Un pense\-bête typique contient des informations écrites sur un petit morceau de papier de couleur, collé ensuite sur un document.  Les pense\-bêtes numériques fournissent des fonctionnalités similaires dans les documents électroniques, tout en permettant en plus d'inclure de nombreux autres types de contenu tel que du texte saisi au clavier, des notes manuscrites \(par exemple, des traits "d'encre" [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]\) ou des liens Web.  
  
 L'illustration suivante montre quelques exemples d'annotations sous forme de mises en surbrillance, de pense\-bêtes ou de remarques manuscrites.  
  
 ![Annotations pense&#45;bête manuscrites et texte en surbrillance](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF\_StickyNote")  
  
 L'exemple suivant illustre la méthode que vous pouvez utiliser pour activer la prise en charge des annotations dans votre application.  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## Mises en surbrillance  
 On utilise diverses méthodes créatives pour attirer l'attention sur des éléments présentant un intérêt particulier sur un document papier, par exemple on peut souligner, surligner, encercler des mots dans une phrase ou tracer des marques ou des annotations en marge.  Les annotations en surbrillance dans [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] fournissent une fonctionnalité similaire pour marquer des informations affichées dans des contrôles d'affichage de document [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 L'illustration suivante montre un exemple d'annotation en surbrillance.  
  
 ![Annotation en surbrillance](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF\_Callouts")  
  
 Les utilisateurs créent généralement des annotations en sélectionnant du texte ou un élément d'intérêt, puis ils cliquent avec le bouton droit pour afficher un <xref:System.Windows.Controls.ContextMenu> contenant des options d'annotation.  L'exemple suivant illustre le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que vous pouvez utiliser pour déclarer un <xref:System.Windows.Controls.ContextMenu> contenant les commandes routées auxquelles les utilisateurs peuvent accéder pour créer et gérer des annotations.  
  
 [!code-xml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## Ancrage de données  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] lie des annotations aux données que l'utilisateur sélectionne, pas seulement à une position dans l'affichage.  Par conséquent, en cas de modification de la vue du document, par exemple si l'utilisateur fait défiler ou redimensionne la fenêtre d'affichage, l'annotation suit la sélection des données à laquelle elle est liée.  Par exemple, le graphique suivant illustre une annotation que l'utilisateur a faite sur une sélection de texte.  En cas de modification de la vue du document \(défilements, redimensionnements, mises à l'échelle ou tout autre déplacement\), l'annotation en surbrillance est déplacée avec la sélection des données d'origine.  
  
 ![Ancrage des données de l'annotation](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF\_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## Mise en correspondance des annotations avec les objets annotés  
 Vous pouvez faire correspondre des annotations aux objets annotés associés.  Prenez, par exemple, une application de lecture de document simple comportant un volet de commentaires.  Le volet de commentaires peut être une zone de liste qui affiche le texte à partir d'une liste d'annotations ancrées à un document.  Si l'utilisateur sélectionne un élément dans la zone de liste, l'application affiche le paragraphe dans le document auquel l'objet annotation correspondant est ancré.  
  
 L'exemple ci\-dessous montre comment implémenter le gestionnaire d'événements d'une telle zone de liste qui sert de volet de commentaires :  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 Un autre exemple de scénario implique des applications qui activent l'échange d'annotations et de pense\-bêtes entre des lecteurs de document par le biais de la messagerie électronique.  Cette fonction permet à ces applications de conduire le lecteur à la page contenant l'annotation échangée.  
  
## Voir aussi  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>   
 <xref:System.Windows.Controls.DocumentViewer>   
 <xref:System.Windows.Controls.FlowDocumentPageViewer>   
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>   
 <xref:System.Windows.Controls.FlowDocumentReader>   
 <xref:System.Windows.Annotations.IAnchorInfo>   
 [Schéma d'annotations](../../../../docs/framework/wpf/advanced/annotations-schema.md)   
 [Vue d'ensemble de ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-overview.md)   
 [Vue d'ensemble des commandes](../../../../docs/framework/wpf/advanced/commanding-overview.md)   
 [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [How to: Add a Command to a MenuItem](http://msdn.microsoft.com/fr-fr/013d68a0-5373-4a68-bd91-5de574307370)