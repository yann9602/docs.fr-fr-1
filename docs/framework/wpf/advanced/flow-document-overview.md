---
title: "Vue d&#39;ensemble des documents dynamiques | Microsoft Docs"
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
  - "schéma de contenu"
  - "documents, documents dynamiques"
  - "éléments de contenu de flux (WPF), documents dynamiques"
  - "documents dynamiques"
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Vue d&#39;ensemble des documents dynamiques
Les documents dynamiques sont conçus pour optimiser l'affichage et la lisibilité.  Au lieu d'avoir une disposition prédéfinie, ces documents ajustent et refluent dynamiquement leur contenu en fonction des variables d'exécution telles que la taille de la fenêtre, la résolution du périphérique et les préférences de l'utilisateur \(en option\).  En outre, les documents dynamiques offrent des fonctionnalités de document avancées, telles que la pagination et les colonnes.  Cette rubrique donne une vue d'ensemble des documents dynamiques et explique comment les créer.  
  
   
  
<a name="what_is_a_flow_document"></a>   
## Description d'un document dynamique  
 Un document dynamique est conçu pour gérer le rendu du contenu en fonction de la taille de la fenêtre, la résolution du périphérique et d'autres variables d'environnement.  En outre, les documents dynamiques possèdent plusieurs fonctionnalités intégrées, par exemple la recherche, les modes d'affichage, qui optimisent la lisibilité et permettent de changer la taille et l'apparence des polices.  Les documents dynamiques sont utilisés surtout lorsque la facilité de lecture est le scénario principal de consommation des documents.  À l'inverse, les documents fixes sont conçus pour avoir une présentation statique.  Ces documents sont utiles lorsque le contenu source doit être fidèlement respecté.  Pour plus d'informations sur les différents types de documents, consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 Les schémas ci\-dessous montrent un exemple de document dynamique affiché dans des fenêtres de différentes tailles.  À chaque fois que la zone d'affichage change, le contenu reflue pour utiliser de façon optimale l'espace disponible.  
  
 ![Nouveau flux de contenu d'un document dynamique](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs\_FlowDocument")  
  
 Comme vous le voyez sur les schémas ci\-dessus, le contenu dynamique peut comprendre plusieurs composants, notamment des paragraphes, des listes, des images et bien plus encore.  Ces composants correspondent à des éléments dans le balisage et à des objets dans le code procédural.  Nous étudierons ces classes en détail dans la section [Classes liées au contenu dynamique](#flow_related_classes) de ce document.  Pour le moment, voici un exemple de code simple qui crée un document dynamique comprenant un paragraphe avec du texte en gras et une liste.  
  
 [!code-xml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 Cet extrait de code est illustré ci\-dessous.  
  
 ![Capture d'écran : exemple d'affichage de FlowDocument](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow\_Ovw\_First\_Example")  
  
 Dans cet exemple, le contrôle <xref:System.Windows.Controls.FlowDocumentReader> est utilisé pour héberger le contenu dynamique.  Pour plus d'informations sur les contrôles servant à héberger le contenu dynamique, consultez la section [Types de documents dynamiques](#flow_document_types).  Les éléments <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem> et <xref:System.Windows.Documents.Bold> sont utilisés pour gérer la mise en forme du contenu, selon leur ordre dans le balisage.  Par exemple, l'élément <xref:System.Windows.Documents.Bold> s'étend uniquement sur une partie du texte dans le paragraphe ; par conséquent, seule cette partie du texte apparaît en gras.  Si vous avez déjà utilisé le langage HTML, cela doit vous sembler familier.  
  
 Comme le montre l'illustration ci\-dessus, plusieurs fonctionnalités sont intégrées aux documents dynamiques :  
  
-   Recherche : permet à l'utilisateur d'effectuer une recherche de texte intégral sur l'ensemble d'un document.  
  
-   Mode d'affichage : l'utilisateur peut sélectionner son mode d'affichage préféré parmi le mode d'affichage page unique \(page par page\), deux pages à la fois \(format livre ouvert\) ou le mode d'affichage défilement continu \(sans marge inférieure\).  Pour plus d'informations sur les modes d'affichage, consultez <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
-   Contrôles de navigation des pages : si le mode d'affichage du document utilise des pages, les contrôles de navigation des pages incluent un bouton pour accéder à la page suivante \(flèche Bas\) ou à la page précédente \(flèche Haut\), ainsi qu'une indication du numéro de la page active et du nombre total de pages.  Vous pouvez aussi faire défiler les pages à l'aide des touches de direction du clavier.  
  
-   Zoom : les contrôles de zoom permettent à l'utilisateur d'augmenter ou de diminuer le niveau de zoom en cliquant sur les boutons PLUS ou MOINS, respectivement.  Les contrôles de zoom incluent également un curseur pour ajuster le niveau de zoom.  Pour plus d'informations, consultez <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Ces fonctionnalités peuvent être modifiées selon le contrôle utilisé pour héberger le contenu dynamique.  La section suivante décrit les différents contrôles.  
  
<a name="flow_document_types"></a>   
## Types de documents dynamiques  
 L'affichage et l'apparence du contenu des documents dynamiques dépendent de l'objet utilisé pour héberger le contenu dynamique.  Il existe quatre contrôles qui prennent en charge l'affichage du contenu dynamique : <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  Ces contrôles sont brièvement décrits ci\-après.  
  
 **Remarque :**  <xref:System.Windows.Documents.FlowDocument> est requis pour héberger directement le contenu dynamique, donc tous ces contrôles d'affichage utilisent un <xref:System.Windows.Documents.FlowDocument> pour activer l'hébergement du contenu dynamique.  
  
### FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> inclut des fonctionnalités qui permettent à l'utilisateur de choisir dynamiquement entre plusieurs modes d'affichage : mode d'affichage page unique \(page par page\), deux pages à la fois \(format livre ouvert\) et mode d'affichage défilement continu \(sans marge inférieure\).  Pour plus d'informations sur les modes d'affichage, consultez <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Si vous n'avez pas besoin de basculer dynamiquement entre les différents modes d'affichage, <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer> fournissent des versions plus allégées d'afficheurs de contenu dynamique qui sont réglées sur un mode d'affichage particulier.  
  
### FlowDocumentPageViewer et FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> affiche le contenu en mode page par page, alors que <xref:System.Windows.Controls.FlowDocumentScrollViewer> affiche le contenu en mode de défilement continu.  <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer> correspondent chacun à un mode d'affichage particulier.  En revanche, <xref:System.Windows.Controls.FlowDocumentReader> inclut des fonctionnalités qui permettent à l'utilisateur de choisir dynamiquement entre plusieurs modes d'affichage \(tels que ceux fournis par l'énumération <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>\), mais qui en font une application qui consomment beaucoup plus de ressources que <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Par défaut, une barre de défilement verticale est toujours affichée et une barre de défilement horizontale apparaît si nécessaire.  L'interface utilisateur par défaut pour <xref:System.Windows.Controls.FlowDocumentScrollViewer> n'inclut pas de barre d'outils ; toutefois, vous pouvez utiliser la propriété <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> pour activer une barre d'outils intégrée.  
  
### RichTextBox  
 Utilisez <xref:System.Windows.Controls.RichTextBox> lorsque vous souhaitez autoriser l'utilisateur à modifier le contenu dynamique.  Par exemple, si vous voulez créer un éditeur qui autorise l'utilisateur à manipuler des éléments tels que les tableaux, les mises en forme \(italique, gras\), etc, vous devez utiliser <xref:System.Windows.Controls.RichTextBox>.  Pour plus d'informations, consultez [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md).  
  
 **Remarque :** un contenu dynamique placé dans un <xref:System.Windows.Controls.RichTextBox> ne se comporte pas tout à fait de la même façon qu'un contenu dynamique dans d'autres contrôles.  Par exemple, <xref:System.Windows.Controls.RichTextBox> ne comporte pas de colonnes et ne permet donc pas de redimensionnement automatique.  Par ailleurs, <xref:System.Windows.Controls.RichTextBox> ne dispose pas des fonctionnalités généralement intégrées au contenu dynamique, telles que la recherche, le mode d'affichage, la navigation entre les pages et le zoom.  
  
<a name="creating_flow_content"></a>   
## Création de contenu dynamique  
 Le contenu dynamique peut être complexe et comprendre des éléments variés, notamment du texte, des images, des tableaux et même des classes dérivées <xref:System.Windows.UIElement>, par exemple des contrôles.  Pour comprendre comment créer du contenu dynamique complexe, les points suivants sont essentiels :  
  
-   **Classes liées au contenu dynamique** : chaque classe utilisée dans le contenu dynamique a un rôle spécifique.  En outre, la relation hiérarchique entre les classes vous aide à comprendre comment les utiliser.  Par exemple, les classes dérivées de la classe <xref:System.Windows.Documents.Block> sont utilisées pour contenir d'autres objets alors que les classes dérivées de <xref:System.Windows.Documents.Inline> contiennent des objets affichés.  
  
-   **Schéma du contenu** : un document dynamique peut nécessiter un nombre important d'éléments imbriqués.  Le schéma du contenu indique les relations parent\/enfant possibles entre les éléments.  
  
 Les sections suivantes décrivent en détail chacun des points ci\-dessus.  
  
<a name="flow_related_classes"></a>   
## Classes liées au contenu dynamique  
 Le diagramme ci\-dessous contient les objets les plus souvent utilisés avec du contenu dynamique :  
  
 ![Diagramme : hiérarchie de classe d'élément de contenu de flux](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow\_Class\_Hierarchy")  
  
 Pour faciliter la gestion du contenu dynamique, les objets sont classés dans deux catégories principales :  
  
1.  **Classes dérivées de Block** : elles sont également appelées « éléments de contenu Block » ou simplement « éléments Block ».  Les éléments qui héritent de la classe <xref:System.Windows.Documents.Block> peuvent être utilisés pour grouper des éléments sous un parent commun ou appliquer des attributs communs à un groupe.  
  
2.  **Classes dérivées de Inline** : elles sont également appelées « éléments de contenu Inline » ou simplement « éléments Inline ».  Les éléments qui héritent de la classe <xref:System.Windows.Documents.Inline> sont soit contenus dans un élément Block, soit un autre élément Inline.  Les éléments Inline sont souvent utilisés comme conteneur direct pour le contenu restitué sur l'écran.  Par exemple, un <xref:System.Windows.Documents.Paragraph> \(élément Block\) peut contenir un <xref:System.Windows.Documents.Run> \(élément Inline\), mais le <xref:System.Windows.Documents.Run> contient en fait le texte restitué sur l'écran.  
  
 Chaque classe de ces deux catégories est brièvement décrite ci\-après.  
  
### Classes dérivées de Block  
 **Paragraph**  
  
 <xref:System.Windows.Documents.Paragraph> est généralement utilisé pour grouper le contenu dans un paragraphe.  L'utilisation la plus courante et la plus simple de Paragraph consiste à créer un paragraphe de texte.  
  
 [!code-xml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 Cependant, vous pouvez également inclure des éléments dérivés de Inline, comme vous le verrez ci\-dessous.  
  
 **Section**  
  
 <xref:System.Windows.Documents.Section> est utilisé uniquement pour contenir d'autres éléments dérivés de <xref:System.Windows.Documents.Block>.  Il n'applique pas toute mise en forme par défaut aux éléments qu'il contient.  Toutefois, les valeurs de propriété affectées à un <xref:System.Windows.Documents.Section> s'appliquent à ses éléments enfants.  Une section vous permet également d'itérer par programmation au sein de sa collection enfant.  <xref:System.Windows.Documents.Section> est utilisé de façon semblable à la balise \< DIV \> en HTML.  
  
 Dans l'exemple ci\-dessous, trois paragraphes sont définis sous un <xref:System.Windows.Documents.Section>.  La propriété <xref:System.Windows.Documents.TextElement.Background%2A> de la section a la valeur Rouge, par conséquent la couleur d'arrière\-plan des paragraphes est également rouge.  
  
 [!code-xml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> permet aux éléments <xref:System.Windows.UIElement> \(c.\-à\-d.  un <xref:System.Windows.Controls.Button>\) d'être incorporés dans un contenu de flux dérivé d'un bloc.  <xref:System.Windows.Documents.InlineUIContainer> \(voir ci\-dessous\) est utilisé pour incorporer des éléments <xref:System.Windows.UIElement> dans un contenu de flux inline.  <xref:System.Windows.Documents.BlockUIContainer> et <xref:System.Windows.Documents.InlineUIContainer> sont  importants, car il n'existe pas d'autre façon d'utiliser un <xref:System.Windows.UIElement> dans le contenu de flux à moins qu'il soit contenu dans l'un de ces deux éléments.  
  
 L'exemple suivant montre comment utiliser l'élément <xref:System.Windows.Documents.BlockUIContainer> pour héberger des objets <xref:System.Windows.UIElement> dans le contenu dynamique.  
  
 [!code-xml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : UIElement incorporé dans le contenu du flux](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **Liste**  
  
 <xref:System.Windows.Documents.List> est utilisé pour créer une liste numérique ou à puces.  Affectez à la propriété <xref:System.Windows.Documents.List.MarkerStyle%2A> une valeur d'énumération <xref:System.Windows.TextMarkerStyle> pour déterminer le style de la liste.  L'exemple ci\-dessous montre comment créer une liste simple.  
  
 [!code-xml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Remarque :** <xref:System.Windows.Documents.List> est le seul élément de flux qui utilise <xref:System.Windows.Documents.ListItemCollection> pour gérer les éléments enfants.  
  
 **Table**  
  
 <xref:System.Windows.Documents.Table> est utilisé pour créer une table.  <xref:System.Windows.Documents.Table> est identique à l'élément <xref:System.Windows.Controls.Grid> mais il présente davantage de fonctionnalités et, par conséquent, requiert une charge de ressources plus importante.  Comme <xref:System.Windows.Controls.Grid> est un <xref:System.Windows.UIElement>, il ne peut pas être utilisé dans le contenu dynamique sauf s'il est contenu dans un <xref:System.Windows.Documents.BlockUIContainer> ou <xref:System.Windows.Documents.InlineUIContainer>.  Pour plus d'informations sur <xref:System.Windows.Documents.Table>, consultez [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
### Classes dérivées de Inline  
 **Run**  
  
 <xref:System.Windows.Documents.Run> est utilisé pour contenir du texte non mis en forme.  Vous pouvez vous attendre à ce que les objets <xref:System.Windows.Documents.Run> soient largement utilisés dans le contenu de flux.  Toutefois, les éléments <xref:System.Windows.Documents.Run> ne doivent pas être obligatoirement utilisés de manière explicite dans le balisage.  <xref:System.Windows.Documents.Run> doit obligatoirement être utilisé lorsque vous créez ou manipulez des documents dynamiques à l'aide du code.  Par exemple, dans le balisage ci\-dessous, le premier <xref:System.Windows.Documents.Paragraph> spécifie explicitement l'élément <xref:System.Windows.Documents.Run>, mais pas le second.  Les deux paragraphes génèrent le même résultat.  
  
 [!code-xml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Remarque :**  démarrer dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], la propriété <xref:System.Windows.Documents.Run.Text%2A> de l'objet <xref:System.Windows.Documents.Run> est une propriété de dépendance.  Vous pouvez lier la propriété <xref:System.Windows.Documents.Run.Text%2A> à une source de données, telle qu'un <xref:System.Windows.Controls.TextBlock>.  La propriété <xref:System.Windows.Documents.Run.Text%2A> prend complètement en charge la liaison unidirectionnelle.  La propriété <xref:System.Windows.Documents.Run.Text%2A> prend également en charge la liaison bidirectionnelle, à l'exception de <xref:System.Windows.Controls.RichTextBox>.  Pour obtenir un exemple, consultez <xref:System.Windows.Documents.Run.Text%2A?displayProperty=fullName>.  
  
 **Span**  
  
 <xref:System.Windows.Documents.Span> regroupe d'autres éléments de contenu inline.  Aucun rendu inhérent n'est appliqué au contenu dans un élément <xref:System.Windows.Documents.Span>.  Toutefois, les éléments hérités de <xref:System.Windows.Documents.Span>, notamment <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> et <xref:System.Windows.Documents.Underline> appliquent la mise en forme au texte.  
  
 Dans l'exemple ci\-dessous, <xref:System.Windows.Documents.Span> est utilisé pour contenir du contenu Inline comprenant du texte, un élément <xref:System.Windows.Documents.Bold> et un <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 La capture d'écran suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : exemple d'affichage de Span](../../../../docs/framework/wpf/advanced/media/flow-spanexample.png "Flow\_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> permet aux éléments <xref:System.Windows.UIElement> \(c.\-à\-d.  un contrôle tel que <xref:System.Windows.Controls.Button>\) d'être incorporé dans un élément de contenu <xref:System.Windows.Documents.Inline>.  Cet élément est l'équivalent Inline de l'élément <xref:System.Windows.Documents.BlockUIContainer> décrit ci\-dessus.  Dans l'exemple ci\-dessous, <xref:System.Windows.Documents.InlineUIContainer> est utilisé pour insérer un <xref:System.Windows.Controls.Button> Inline dans un <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Remarque :** <xref:System.Windows.Documents.InlineUIContainer> ne doit pas nécessairement être utilisé explicitement dans le balisage.  Si vous l'omettez, un <xref:System.Windows.Documents.InlineUIContainer> sera créé quand même lors de la compilation du code.  
  
 **Figure et Floater**  
  
 <xref:System.Windows.Documents.Figure> et <xref:System.Windows.Documents.Floater> sont utilisés pour incorporer le contenu dans les documents dynamiques avec des propriétés de positionnement qui peuvent être personnalisées indépendamment du flux de contenu principal.  Les éléments <xref:System.Windows.Documents.Figure> ou <xref:System.Windows.Documents.Floater> sont souvent utilisés pour mettre en surbrillance ou accentuer des parties de contenu, héberger des images de support ou d'autre contenu au sein du flux de contenu principal ou injecter du contenu lié, tel que des publicités.  
  
 L'exemple suivant montre comment incorporer un élément <xref:System.Windows.Documents.Figure> dans un paragraphe du texte.  
  
 [!code-xml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : exemple de figure](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow\_Ovw\_Figure\_Example")  
  
 <xref:System.Windows.Documents.Figure> et <xref:System.Windows.Documents.Floater> ont des caractéristiques très différentes et sont utilisés pour des scénarios différents.  
  
 **Illustration :**  
  
-   Positionnable : vous pouvez placer ses ancres horizontale et verticale de façon à l'ancrer par rapport à la page, au contenu, à la colonne ou au paragraphe.  Vous pouvez également utiliser ses propriétés <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> et <xref:System.Windows.Documents.Figure.VerticalOffset%2A> pour spécifier des offsets arbitraires.  
  
-   Dimensionnable sur plusieurs colonnes : vous pouvez définir la hauteur et la largeur de <xref:System.Windows.Documents.Figure> sous forme de multiples d'une hauteur ou largeur de page, de contenu ou de colonne.  Notez que dans les deux premiers cas, les multiples supérieurs à 1 ne sont pas autorisés.  Par exemple, vous pouvez définir la largeur d'une <xref:System.Windows.Documents.Figure> en lui affectant la valeur « page 0.5 » ou « contenu 0.25 » ou « colonne 2 ».  Vous pouvez également définir la hauteur et la largeur à des valeurs en pixels absolues.  
  
-   Non paginable : si le contenu d'une <xref:System.Windows.Documents.Figure> ne tient pas dans une <xref:System.Windows.Documents.Figure>, le contenu excédentaire est perdu.  
  
 **Floater :**  
  
-   Non positionnable : cet élément s'affiche dans l'espace disponible, quel qu'il soit.  Vous ne pouvez pas définir l'offset ou ancrer un <xref:System.Windows.Documents.Floater>.  
  
-   Non dimensionnable sur plusieurs colonnes : par défaut, <xref:System.Windows.Documents.Floater> est dimensionné sur une colonne.  Il dispose d'une propriété <xref:System.Windows.Documents.Floater.Width%2A> qui peut être définie sur une valeur en pixels absolue, mais si cette valeur est supérieure à une largeur de colonne, elle est ignorée et le floater est dimensionné sur une colonne.  Vous pouvez le dimensionner sur moins d'une colonne en définissant la largeur en pixels correcte, mais le dimensionnement n'est pas relatif à la colonne, donc « 0.5Column » n'est pas une expression valide pour la largeur <xref:System.Windows.Documents.Floater>.  <xref:System.Windows.Documents.Floater> n'a aucune propriété de hauteur et sa hauteur ne peut pas être définie, sa hauteur dépend du contenu  
  
-   <xref:System.Windows.Documents.Floater> peut être paginé : si, à la largeur spécifiée, son contenu dépasse la hauteur d'une colonne, le floater se divise et la pagination reprend sur la colonne suivante, la page suivante, etc.  
  
 <xref:System.Windows.Documents.Figure> est un emplacement idéal pour placer du contenu autonome lorsque vous souhaitez contrôler la taille et le positionnement et que vous êtes certain qu'il s'adaptera à la taille spécifiée.  <xref:System.Windows.Documents.Floater> est un emplacement idéal pour du contenu plus libre semblable au contenu de la page principale, mais qui en est séparé.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> insère un saut de ligne dans le contenu du flux.  L'exemple suivant illustre l'utilisation du mot clé <xref:System.Windows.Documents.LineBreak> :  
  
 [!code-xml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 La capture d'écran suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : exemple de LineBreak](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow\_Ovw\_LineBreakExample")  
  
### Éléments de collection de flux  
 Dans plusieurs des exemples ci\-dessus, les éléments <xref:System.Windows.Documents.BlockCollection> et <xref:System.Windows.Documents.InlineCollection> sont utilisés pour construire du contenu dynamique par programmation.  Par exemple, pour ajouter des éléments à <xref:System.Windows.Documents.Paragraph>, vous pouvez utiliser la syntaxe suivante :  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Cela ajoute un <xref:System.Windows.Documents.Run> à <xref:System.Windows.Documents.InlineCollection> de <xref:System.Windows.Documents.Paragraph>.  L'effet produit est le même qu'avec le <xref:System.Windows.Documents.Run> implicite situé dans un <xref:System.Windows.Documents.Paragraph> dans le balisage :  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Pour montrer l'utilisation de <xref:System.Windows.Documents.BlockCollection>, l'exemple suivant crée un nouveau <xref:System.Windows.Documents.Section> et utilise la méthode **Add** pour ajouter un nouveau <xref:System.Windows.Documents.Paragraph> au contenu de <xref:System.Windows.Documents.Section>.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 En plus d'ajouter des éléments à une collection de flux, vous pouvez aussi en supprimer.  L'exemple suivant supprime le dernier élément <xref:System.Windows.Documents.Inline> de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 L'exemple suivant efface tout le contenu \(éléments <xref:System.Windows.Documents.Inline> de <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Lorsque vous construisez du contenu dynamique par programmation, vous utiliserez certainement très souvent ces collections.  
  
 L'utilisation par un élément de flux d'un <xref:System.Windows.Documents.InlineCollection> \(Inlines\) ou d'un <xref:System.Windows.Documents.BlockCollection> \(Blocks\) pour contenir ses éléments enfants dépend du type d'éléments enfants \(<xref:System.Windows.Documents.Block> ou <xref:System.Windows.Documents.Inline>\) qui peut être contenu par le parent.  Les règles relatives à la relation contenant\-contenu pour les éléments de contenu dynamique sont résumées dans le schéma du contenu présenté à la section suivante.  
  
 **Remarque :** il existe un troisième type de collection utilisée avec le contenu dynamique, <xref:System.Windows.Documents.ListItemCollection>, mais cette collection est utilisée uniquement avec <xref:System.Windows.Documents.List>.  En outre, il existe plusieurs collections utilisées avec <xref:System.Windows.Documents.Table>.  Pour plus d'informations, consultez [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
<a name="content_schema"></a>   
## Schéma du contenu  
 Vu le nombre important d'éléments de contenu dynamique, il est parfois difficile de savoir quel type d'éléments enfants peut être contenu dans un élément.  Le schéma ci\-dessous résume les règles relatives à la relation contenant\-contenu pour les éléments de contenu dynamique.  Les flèches représentent les relations parent\/enfants possibles.  
  
 ![Diagramme : schéma de relation contenant&#45;contenu du flux](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow\_Content\_Schema")  
  
 Comme vous pouvez le constater sur le schéma ci\-dessus, les enfants autorisés pour un élément ne sont pas nécessairement déterminés par le fait qu'il s'agisse d'un élément <xref:System.Windows.Documents.Block> ou d'un élément <xref:System.Windows.Documents.Inline>.  Par exemple, <xref:System.Windows.Documents.Span> \(élément <xref:System.Windows.Documents.Inline>\) peut avoir uniquement des éléments enfants <xref:System.Windows.Documents.Inline> alors que <xref:System.Windows.Documents.Figure> \(également un élément <xref:System.Windows.Documents.Inline>\) ne peut avoir que des éléments enfants <xref:System.Windows.Documents.Block>.  Par conséquent, ce schéma est très utile pour savoir rapidement quel élément peut être contenu dans un autre.  Par exemple, utilisons le schéma pour déterminer comment construire le contenu dynamique d'un <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** Un <xref:System.Windows.Controls.RichTextBox> doit contenir un<xref:System.Windows.Documents.FlowDocument> qui doit à son tour contenir un objet dérivé de <xref:System.Windows.Documents.Block>.  Voici le segment correspondant extrait du schéma ci\-dessus.  
  
 ![Diagramme : règles de relation contenant&#45;contenu RichtextBox](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow\_Ovw\_SchemaWalkThrough1")  
  
 À ce stade, le balisage peut ressembler à ceci.  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** D'après le schéma, plusieurs éléments <xref:System.Windows.Documents.Block> peuvent être sélectionnés, notamment <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List> et <xref:System.Windows.Documents.BlockUIContainer> \(voir classes dérivées de Block ci\-dessus\).  Supposons que nous voulons l'élément <xref:System.Windows.Documents.Table>.  Le schéma ci\-dessus indique qu'un <xref:System.Windows.Documents.Table> contient un <xref:System.Windows.Documents.TableRowGroup> contenant des éléments <xref:System.Windows.Documents.TableRow>, qui contiennent des éléments <xref:System.Windows.Documents.TableCell> contenant eux\-mêmes un objet dérivé de <xref:System.Windows.Documents.Block>.  Pour <xref:System.Windows.Documents.Table>, voici le segment correspondant extrait du schéma ci\-dessus.  
  
 ![Diagramme : schéma parent&#47;enfant pour Table](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow\_Ovw\_SchemaWalkThrough2")  
  
 Le balisage correspondant est indiqué ci\-dessous.  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Ici encore, un ou plusieurs éléments <xref:System.Windows.Documents.Block> sont requis sous <xref:System.Windows.Documents.TableCell>.  Pour simplifier, insérons du texte dans la cellule.  Pour cela, nous pouvons utiliser un <xref:System.Windows.Documents.Paragraph> avec un élément <xref:System.Windows.Documents.Run>.  Voici les segments correspondants extraits du schéma ci\-dessus ; ils montrent qu'un <xref:System.Windows.Documents.Paragraph> peut contenir un élément <xref:System.Windows.Documents.Inline> et qu'un <xref:System.Windows.Documents.Run> \(élément <xref:System.Windows.Documents.Inline>\) peut uniquement contenir du texte brut.  
  
 ![Diagramme : schéma parent&#47;enfant pour Paragraph](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow\_Ovw\_SchemaWalkThrough3")  
  
 ![Diagramme : schéma parent&#47;enfant pour Run](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow\_Ovw\_SchemaWalkThrough4")  
  
 Le balisage de l'exemple complet est indiqué ci\-dessous.  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## Personnalisation du texte  
 Généralement, le texte est le type de contenu le plus fréquent dans un document dynamique.  Même si les objets décrits ci\-dessus permettent de contrôler la plupart des aspects concernant la restitution du texte, il existe d'autres méthodes, décrites dans cette section, destinées à personnaliser le texte.  
  
### Ornements de texte  
 Les ornements de texte vous permettent d'appliquer au texte les effets suivants : souligné, ligne au\-dessus, ligne de base et barré \(voir les images ci\-dessous\).  Ces ornements sont ajoutés à l'aide de la propriété <xref:System.Windows.Documents.Inline.TextDecorations%2A> qui est exposée par plusieurs objets, y compris <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Controls.TextBox>.  
  
 L'exemple suivant montre comment paramétrer la propriété <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> d'un <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : texte avec effet barré par défaut](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline\_TextDec\_Strike")  
  
 Les illustrations suivantes affichent les rendus respectifs des ornements **Overline** \(ligne au\-dessus\), **Baseline** \(ligne de base\) et **Underline** \(souligné\).  
  
 ![Capture d'écran : Overline TextDecorator](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline\_TextDec\_Over")  
  
 ![Capture d'écran : effet de la ligne de base par défaut sur le texte](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline\_TextDec\_Base")  
  
 ![Capture d'écran : texte avec effet souligné par défaut](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline\_TextDec\_Under")  
  
### Typographie  
 La propriété <xref:System.Windows.Documents.TextElement.Typography%2A> est exposée par la plupart du contenu dynamique, y compris <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Controls.TextBox>.  Cette propriété est utilisée pour contrôler les caractéristiques\/variations typographiques de texte \(c.\-à\-d.  petites ou grandes majuscules, exposants et indices, etc\).  
  
 L'exemple suivant montre comment définir l'attribut <xref:System.Windows.Documents.TextElement.Typography%2A> en utilisant l'élément <xref:System.Windows.Documents.Paragraph> comme exemple.  
  
 [!code-xml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 L'illustration suivante montre comment s'affiche cet exemple.  
  
 ![Capture d'écran : texte avec typographie altérée](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement\_Typog")  
  
 Par contraste, l'illustration suivante montre comment s'affiche un exemple similaire avec des propriétés typographiques par défaut.  
  
 ![Capture d'écran : texte avec typographie altérée](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement\_Typog\_Default")  
  
 L'exemple suivant montre comment définir la propriété <xref:System.Windows.Controls.TextBox.Typography%2A> par programmation.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 Pour plus d'informations sur la typographie, consultez [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
## Voir aussi  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)   
 [Vue d'ensemble du modèle de contenu de TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)   
 [Vue d'ensemble de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de Table](../../../../docs/framework/wpf/advanced/table-overview.md)   
 [Vue d'ensemble des annotations](../../../../docs/framework/wpf/advanced/annotations-overview.md)