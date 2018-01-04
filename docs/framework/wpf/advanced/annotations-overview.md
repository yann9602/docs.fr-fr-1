---
title: Vue d'ensemble des annotations
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe3f0caa8f23a3b68f1017254a770af766f83f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="annotations-overview"></a><span data-ttu-id="40f49-102">Vue d'ensemble des annotations</span><span class="sxs-lookup"><span data-stu-id="40f49-102">Annotations Overview</span></span>
<span data-ttu-id="40f49-103">Écrire des notes ou des commentaires sur des documents papier est une activité si banale que nous pensons qu’elle va de soi.</span><span class="sxs-lookup"><span data-stu-id="40f49-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="40f49-104">Ces notes ou commentaires sont des « annotations » que nous ajoutons à un document pour marquer des informations ou mettre en évidence des éléments présentant un intérêt particulier afin de nous y référer plus tard.</span><span class="sxs-lookup"><span data-stu-id="40f49-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="40f49-105">Bien que la rédaction de notes sur des documents imprimés soit une tâche simple et banale, la possibilité d’ajouter des commentaires personnels à des documents électroniques, quand cette fonctionnalité est disponible, est généralement très limitée.</span><span class="sxs-lookup"><span data-stu-id="40f49-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="40f49-106">Cette rubrique passe en revue plusieurs types d’annotation courants, en particulier les pense-bêtes et les mises en surbrillance. Elle explique en quoi [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] simplifie ces types d’annotation dans les applications via les contrôles d’affichage de document [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40f49-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] facilitates these types of annotations in applications through the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] document viewing controls.</span></span>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="40f49-107">incluent des contrôles d’affichage de document qui prennent en charge les annotations <xref:System.Windows.Controls.FlowDocumentReader> et <xref:System.Windows.Controls.FlowDocumentScrollViewer>, ainsi que les contrôles dérivés de <xref:System.Windows.Controls.Primitives.DocumentViewerBase> comme <xref:System.Windows.Controls.DocumentViewer> et <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span><span class="sxs-lookup"><span data-stu-id="40f49-107"> document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a><span data-ttu-id="40f49-108">Pense-bêtes</span><span class="sxs-lookup"><span data-stu-id="40f49-108">Sticky Notes</span></span>  
 <span data-ttu-id="40f49-109">Un pense-bête classique contient des informations écrites sur un petit bout de papier de couleur, « collé » ensuite sur un document.</span><span class="sxs-lookup"><span data-stu-id="40f49-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="40f49-110">Les pense-bêtes numériques fournissent des fonctionnalités similaires dans les documents électroniques, tout en permettant d’inclure de nombreux autres types de contenu comme du texte tapé au clavier, des notes manuscrites (par exemple des traits « d’encre » [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]) ou des liens web.</span><span class="sxs-lookup"><span data-stu-id="40f49-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="40f49-111">L’illustration suivante montre quelques exemples d’annotations sous forme de mises en surbrillance, de pense-bêtes ou de notes manuscrites.</span><span class="sxs-lookup"><span data-stu-id="40f49-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="40f49-112">![Pense-bêtes de type mise en surbrillance, note tapée et note manuscrite.](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="40f49-112">![Highlight, text and ink sticky note annotations.](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="40f49-113">L’exemple suivant illustre la méthode que vous pouvez utiliser pour activer la prise en charge des annotations dans votre application.</span><span class="sxs-lookup"><span data-stu-id="40f49-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a><span data-ttu-id="40f49-114">Mises en surbrillance</span><span class="sxs-lookup"><span data-stu-id="40f49-114">Highlights</span></span>  
 <span data-ttu-id="40f49-115">Nous utilisons diverses méthodes créatives pour attirer l’attention sur des éléments présentant un intérêt particulier sur un document papier, par exemple en soulignant, en surlignant ou en encerclant des mots dans une phrase, ou en mettant des marques ou des annotations dans la marge.</span><span class="sxs-lookup"><span data-stu-id="40f49-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="40f49-116">Les annotations en surbrillance de [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] fournissent une fonctionnalité similaire pour marquer les informations affichées dans les contrôles d’affichage de document [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="40f49-116">Highlight annotations in [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] provide a similar feature for marking up information displayed in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] document viewing controls.</span></span>  
  
 <span data-ttu-id="40f49-117">L’illustration suivante montre un exemple d’annotation en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="40f49-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="40f49-118">![Annotation en surbrillance](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="40f49-118">![Highlight Annotation](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="40f49-119">Les utilisateurs créent généralement des annotations en sélectionnant du texte ou un élément d’intérêt, puis en cliquant pour afficher un <xref:System.Windows.Controls.ContextMenu> des options d’annotation.</span><span class="sxs-lookup"><span data-stu-id="40f49-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="40f49-120">L’exemple suivant illustre la [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que vous pouvez utiliser pour déclarer un <xref:System.Windows.Controls.ContextMenu> avec les commandes routées auxquelles les utilisateurs peuvent accéder pour créer et gérer des annotations.</span><span class="sxs-lookup"><span data-stu-id="40f49-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a><span data-ttu-id="40f49-121">Ancrage des données</span><span class="sxs-lookup"><span data-stu-id="40f49-121">Data Anchoring</span></span>  
 <span data-ttu-id="40f49-122">[!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] lie les annotations aux données que l’utilisateur sélectionne, pas seulement à une position dans l’affichage.</span><span class="sxs-lookup"><span data-stu-id="40f49-122">The [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="40f49-123">Ainsi, en cas de changement de l’affichage du document, par exemple si l’utilisateur fait défiler ou redimensionne la fenêtre d’affichage, l’annotation suit la sélection de données à laquelle elle est liée.</span><span class="sxs-lookup"><span data-stu-id="40f49-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="40f49-124">Le graphique suivant illustre une annotation que l’utilisateur a faite sur une sélection de texte.</span><span class="sxs-lookup"><span data-stu-id="40f49-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="40f49-125">En cas de changement de l’affichage du document (défilements, redimensionnements, mises à l’échelle ou tout autre type de déplacement), l’annotation en surbrillance se déplace avec la sélection de données d’origine.</span><span class="sxs-lookup"><span data-stu-id="40f49-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="40f49-126">![Ancrage des données d’annotation](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="40f49-126">![Annotation Data Anchoring](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="40f49-127">Mise en correspondance des annotations avec les objets annotés</span><span class="sxs-lookup"><span data-stu-id="40f49-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="40f49-128">Vous pouvez faire correspondre des annotations aux objets annotés associés.</span><span class="sxs-lookup"><span data-stu-id="40f49-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="40f49-129">Par exemple, imaginez une simple application de lecture de document comportant un volet de commentaires.</span><span class="sxs-lookup"><span data-stu-id="40f49-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="40f49-130">Le volet de commentaires peut être une zone de liste qui affiche le texte à partir d’une liste d’annotations ancrées à un document.</span><span class="sxs-lookup"><span data-stu-id="40f49-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="40f49-131">Si l’utilisateur sélectionne un élément dans la zone de liste, l’application affiche le paragraphe du document auquel l’objet d’annotation correspondant est ancré.</span><span class="sxs-lookup"><span data-stu-id="40f49-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="40f49-132">L’exemple ci-dessous montre comment implémenter le gestionnaire d’événements de ce type de zone de liste pour servir de volet de commentaires.</span><span class="sxs-lookup"><span data-stu-id="40f49-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="40f49-133">Dans un autre exemple de scénario, des applications activent l’échange d’annotations et de pense-bêtes entre des lecteurs de documents par e-mail.</span><span class="sxs-lookup"><span data-stu-id="40f49-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through e-mail.</span></span> <span data-ttu-id="40f49-134">Grâce à cette fonctionnalité, les applications peuvent amener le lecteur à la page qui contient l’annotation échangée.</span><span class="sxs-lookup"><span data-stu-id="40f49-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f49-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40f49-135">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>  
 <xref:System.Windows.Controls.DocumentViewer>  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>  
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
 <xref:System.Windows.Controls.FlowDocumentReader>  
 <xref:System.Windows.Annotations.IAnchorInfo>  
 [<span data-ttu-id="40f49-136">Schéma d'annotations</span><span class="sxs-lookup"><span data-stu-id="40f49-136">Annotations Schema</span></span>](../../../../docs/framework/wpf/advanced/annotations-schema.md)  
 [<span data-ttu-id="40f49-137">Vue d’ensemble de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="40f49-137">ContextMenu Overview</span></span>](../../../../docs/framework/wpf/controls/contextmenu-overview.md)  
 [<span data-ttu-id="40f49-138">Vue d’ensemble des commandes</span><span class="sxs-lookup"><span data-stu-id="40f49-138">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="40f49-139">Vue d’ensemble des documents dynamiques</span><span class="sxs-lookup"><span data-stu-id="40f49-139">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="40f49-140">Guide pratique pour ajouter une commande à un MenuItem</span><span class="sxs-lookup"><span data-stu-id="40f49-140">How to: Add a Command to a MenuItem</span></span>](http://msdn.microsoft.com/en-us/013d68a0-5373-4a68-bd91-5de574307370)
