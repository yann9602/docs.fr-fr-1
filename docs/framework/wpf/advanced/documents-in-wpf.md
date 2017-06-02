---
title: "Documents dans WPF | Microsoft Docs"
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
  - "documents consultables dans un navigateur"
  - "documents, consultables dans un navigateur"
  - "documents, contrôles"
  - "documents, empaqueter"
  - "documents, disposition du texte"
  - "documents, types de"
  - "documents, XPS"
  - "empaqueter des documents"
  - "documents XPS"
ms.assetid: 6e8db7bc-050a-4070-aa72-bb8c46e87ff8
caps.latest.revision: 36
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 35
---
# Documents dans WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre une large gamme de fonctionnalités liées aux documents qui permettent de créer du contenu de grande qualité conçu pour être accédé et lu plus facilement que sur les générations précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  En plus d'une amélioration des capacités et de la qualité, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit également des services intégrés pour l'affichage, le conditionnement et la sécurité des documents.  Cette rubrique fournit une introduction sur les types et le conditionnement des documents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
   
  
<a name="types_of_documents"></a>   
## Types de documents  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] divise les documents en deux grandes catégories basées sur leur utilisation prévue ; ces catégories de documents sont appelées « documents fixes » et « documents dynamiques ».  
  
 Les documents fixes sont prévus pour les applications qui requièrent une présentation [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] précise, indépendamment du matériel d'affichage ou d'impression utilisé.  Les documents fixes sont principalement utilisés pour la Publication Assistée par Ordinateur \(PAO\),le traitement de texte et la présentation d'un formulaire, où le respect de la conception de la page d'origine est essentiel.  Dans le cadre de sa disposition, un document fixe conserve l'emplacement de position précis des éléments de contenu indépendamment du périphérique d'affichage ou d'impression utilisé.  Par exemple, un document fixe affiché en 96 points par pouce \(ppp\) apparaît de la même manière que lorsqu'il est imprimé sur une imprimante laser 600 ppp ou une photocomposeuse 4800 ppp.  Dans tous les cas, la disposition de la page reste la même, pendant que la qualité du document s'optimise selon les capacités de chaque périphérique.  
  
 En comparaison, les documents dynamiques sont conçus pour optimiser l'affichage et la lisibilité et trouvent leur meilleure utilisation lorsque la facilité de lecture est le scénario principal de consommation du document.  Au lieu d'avoir une disposition prédéfinie, ces documents ajustent et refluent dynamiquement leur contenu en fonction des variables d'exécution telles que la taille de la fenêtre, la résolution du périphérique et les préférences de l'utilisateur \(en option\).  Une page Web est un exemple simple de page dynamique où le contenu est mis en forme dynamiquement pour s'adapter à la fenêtre active.  Les documents dynamiques optimisent l'expérience d'affichage et de lecture pour l'utilisateur, en fonction de l'environnement au moment de l'exécution.  Par exemple, le même document dynamique se remettra en forme dynamiquement pour une lisibilité optimale sur un écran haute résolution de 19 pouces ou un petit écran d'ANP de 2x3 pouces.  En outre, les documents dynamiques possèdent plusieurs fonctionnalités intégrées, par exemple la recherche, les modes d'affichage, qui optimisent la lisibilité et permettent de changer la taille et l'apparence des polices.  Consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md) pour des illustrations, des exemples et plus d'informations sur les documents dynamiques.  
  
<a name="document_viewer"></a>   
## Contrôles de document et disposition du texte  
 Le [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] fournit un ensemble de contrôles pré\-conçus qui simplifient l'utilisation de documents fixes et dynamiques et de documents de texte dans votre application.  L'affichage du contenu d'un document fixe est pris en charge à l'aide du contrôle <xref:System.Windows.Controls.DocumentViewer>.  L'affichage du contenu d'un document dynamique est pris en charge par trois contrôles différents : <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer> qui mappent sur différents scénarios utilisateur \(voir les sections ci\-dessous\).  D'autres contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournissent une disposition simplifiée pour la prise en charge les utilisations générales de texte \(voir [Texte dans l'interface utilisateur](#text_in_the_user_interface) ci\-dessous\).  
  
### Contrôle de document fixe \- DocumentViewer  
 Le contrôle <xref:System.Windows.Controls.DocumentViewer> est conçu pour afficher le contenu d'un <xref:System.Windows.Documents.FixedDocument>.  Le contrôle <xref:System.Windows.Controls.DocumentViewer> fournit une interface utilisateur intuitive qui fournit une prise en charge intégrée pour les opérations courantes telles que la sortie imprimante, la copie dans le Presse\-papiers, le zoom et les fonctions de recherche de texte.  Le contrôle fournit l'accès aux pages de contenu par le biais d'un mécanisme de défilement familier.  Comme tous les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Controls.DocumentViewer> prend en charge la modification complète ou partielle du style, qui permet au contrôle d'être intégré visuellement dans pratiquement n'importe quelle application ou environnement.  
  
 <xref:System.Windows.Controls.DocumentViewer> est conçu pour afficher le contenu en lecture seule, l'édition ou la modification de contenu n'est pas disponible ni pris en charge.  
  
<a name="flow_document"></a>   
### Contrôles de document dynamique  
 **Remarque :** pour plus d'informations sur les fonctionnalités des documents dynamiques et sur la manière de les créer, consultez [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
 L'affichage du contenu d'un document fixe est pris en charge par trois contrôles : <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
#### FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> inclut des fonctionnalités qui permettent à l'utilisateur de choisir dynamiquement entre plusieurs modes d'affichage : mode d'affichage page unique \(page par page\), deux pages à la fois \(format livre ouvert\) et mode d'affichage défilement continu \(sans marge inférieure\).  Pour plus d'informations sur les modes d'affichage, consultez <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  Si vous n'avez pas besoin de basculer dynamiquement entre les différents modes d'affichage, <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer> fournissent des versions plus allégées d'afficheurs de contenu dynamique qui sont réglées sur un mode d'affichage particulier.  
  
#### FlowDocumentPageViewer et FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> affiche le contenu en mode page par page, alors que <xref:System.Windows.Controls.FlowDocumentScrollViewer> affiche le contenu en mode de défilement continu.  <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer> correspondent chacun à un mode d'affichage particulier.  En revanche, <xref:System.Windows.Controls.FlowDocumentReader> inclut des fonctionnalités qui permettent à l'utilisateur de choisir dynamiquement entre plusieurs modes d'affichage \(tels que ceux fournis par l'énumération <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>\), mais qui en font une application qui consomment beaucoup plus de ressources que <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Par défaut, une barre de défilement verticale est toujours affichée et une barre de défilement horizontale apparaît si nécessaire.  L'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] par défaut pour <xref:System.Windows.Controls.FlowDocumentScrollViewer> n'inclut pas de barre d'outils ; toutefois, vous pouvez utiliser la propriété <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> pour activer une barre d'outils intégrée.  
  
<a name="text_in_the_user_interface"></a>   
### Texte dans l'interface utilisateur  
 En plus d'ajouter du texte aux documents, vous pouvez bien évidemment utiliser du texte dans l'interface utilisateur de l'application, notamment dans les formulaires.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut plusieurs contrôles pour dessiner le texte à l'écran.  Chaque contrôle est ciblé sur un scénario différent et dispose de sa propre liste de fonctionnalités et limitations.  En général, l'élément <xref:System.Windows.Controls.TextBlock> doit être utilisé lorsqu'une prise en charge de texte limitée est requise, par exemple pour une courte phrase dans une [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  <xref:System.Windows.Controls.Label> peut être utilisé lorsqu'une prise en charge de texte minimale est requise.  Pour plus d'informations, consultez [Vue d'ensemble de TextBlock](../../../../docs/framework/wpf/controls/textblock-overview.md).  
  
<a name="packaging"></a>   
## Conditionnement des documents  
 Les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.IO.Packaging> offrent un moyen efficace d'organiser les données d'application, le contenu de document et les ressources associées dans un conteneur unique facile d'accès, portable et facile à distribuer.  Un fichier ZIP est un exemple d'un type de <xref:System.IO.Packaging.Package> capable de contenir plusieurs objets dans une seule unité.  Les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de conditionnement fournissent une implémentation <xref:System.IO.Packaging.ZipPackage> par défaut conçue pour utiliser une norme Open Packaging Conventions avec une architecture de fichiers XML et ZIP.  Les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de conditionnement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] simplifient la création de packages, ainsi que le stockage et l'accès aux objets s'y trouvant.  Un objet stocké dans un <xref:System.IO.Packaging.Package> est référencé sous le nom de <xref:System.IO.Packaging.PackagePart> \("partie"\).  Les packages peuvent également inclure des certificats signés numériquement pouvant être utilisés pour identifier le créateur d'une partie, et pour valider que les contenus d'un package n'ont pas été modifiés.  Les packages comprennent également une fonctionnalité de <xref:System.IO.Packaging.PackageRelationship> qui permet d'ajouter des informations supplémentaires à un package ou d'associer avec des parties spécifiques sans modifier réellement le contenu des parties existantes.  Les services de package prennent aussi en charge [!INCLUDE[TLA#tla_rm](../../../../includes/tlasharptla-rm-md.md)].  
  
 L'architecture de package [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sert de base à de nombreuses technologies clés :  
  
-   Documents [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] conformes au type [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)].  
  
-   Documents au format Microsoft Office « 12 » Open XML \(.docx\).  
  
-   Formats de stockage personnalisés pour votre propre conception d'application.  
  
 En fonction des APIs de packaging, un <xref:System.Windows.Xps.Packaging.XpsDocument> est spécialement conçu pour stocker du contenu de documents fixes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Un <xref:System.Windows.Xps.Packaging.XpsDocument> est un document autonome qui peut être ouvert dans une visionneuse, affiché dans un contrôle <xref:System.Windows.Controls.DocumentViewer>, routé vers un spoule d'impression, ou envoyé directement sur une imprimante compatible avec le format [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
 Les sections suivantes fournissent des informations supplémentaires sur les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.IO.Packaging.Package> et <xref:System.Windows.Xps.Packaging.XpsDocument> fournies avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="packages"></a>   
### Composants d'un package  
 Les APIs de conditionnement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permettent d'organiser les données et documents d'une application dans une seule unité portable.  Un fichier ZIP est l'un des types de package les plus courants et il s'agit du type de package par défaut fourni avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.IO.Packaging.Package> proprement dit est une classe abstraite à partir de laquelle <xref:System.IO.Packaging.ZipPackage> est implémenté à l'aide d'une architecture de fichiers ZIP et XML standard ouverte.  La méthode <xref:System.IO.Packaging.Package.Open%2A> utilise <xref:System.IO.Packaging.ZipPackage> pour créer et utiliser les fichiers ZIP par défaut.  Un package peut contenir trois types d'éléments de base :  
  
|||  
|-|-|  
|<xref:System.IO.Packaging.PackagePart>|Contenu d'application, données, documents et fichiers de ressources.|  
|<xref:System.IO.Packaging.PackageDigitalSignature>|[Certificat X.509](GTMT) pour l'identification, l'authentification et la validation.|  
|<xref:System.IO.Packaging.PackageRelationship>|Des informations ajoutées relatives au package ou à une partie spécifique.|  
  
<a name="PackageParts"></a>   
#### PackageParts  
 Une <xref:System.IO.Packaging.PackagePart> \(« partie »\) est une classe abstraite qui fait référence à un objet stocké dans un <xref:System.IO.Packaging.Package>.  Dans un fichier ZIP, les éléments du package correspondent aux fichiers individuels stockés dans le fichier.  <xref:System.IO.Packaging.ZipPackagePart> fournit l'implémentation par défaut pour les objets sérialisables stockés dans un <xref:System.IO.Packaging.ZipPackage>.  Similaire à un système de fichiers, les parties contenues dans le package sont triées en répertoires hiérarchiques ou « de type dossier ».  En utilisant les APIs de conditionnement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les applications peuvent écrire, stocker et lire plusieurs objets <xref:System.IO.Packaging.PackagePart> à l'aide d'un conteneur de fichier ZIP unique.  
  
<a name="PackageDigitalSignatures"></a>   
#### PackageDigitalSignatures  
 Pour des raisons de sécurité, une <xref:System.IO.Packaging.PackageDigitalSignature> \(« signature numérique »\) peut être associée aux parties dans un package.  Une <xref:System.IO.Packaging.PackageDigitalSignature> incorpore un [509](GTMT) qui fournit deux fonctionnalités :  
  
1.  Identifie et authentifie l'expéditeur de la partie.  
  
2.  Valide que la partie n'a pas été modifiée.  
  
 La signature numérique n'empêche pas la modification de la partie, mais un contrôle de validation contre la signature numérique échoue si la partie est modifiée d'une façon ou d'une autre.  L'application exécute alors l'action appropriée : par exemple, bloquer l'ouverture de la partie, ou notifier l'utilisateur que la partie a été modifiée et n'est pas sécurisée.  
  
<a name="PackageRelationships"></a>   
#### PackageRelationships  
 Une <xref:System.IO.Packaging.PackageRelationship> \("relation"\) fournit un mécanisme permettant d'associer des informations supplémentaires avec le package ou une partie du package.  Une relation est une fonctionnalité de package qui peut associer des informations supplémentaires avec une partie sans modifier le contenu actuel de la partie.  L'insertion directe de nouvelles données dans le contenu de la partie n'est généralement pas très pratique dans de nombreux cas :  
  
-   Le type actuel de la partie et son schéma de contenu ne sont pas connus.  
  
-   Même s'il est connu, le schéma de contenu peut ne pas fournir de moyen d'ajouter des informations supplémentaires.  
  
-   La partie peut être signée numériquement ou chiffrée, empêchant toute modification.  
  
 Les relations de package fournissent un moyen détectable d'ajouter et d'associer des informations supplémentaires avec des parties individuelles ou le package complet.  Les relations de package sont utilisées pour deux fonctions principales :  
  
1.  Définir les relations de dépendance d'une partie à l'autre.  
  
2.  Définir des relations d'information qui ajoutent des notes ou d'autres données relatives à la partie.  
  
 Une <xref:System.IO.Packaging.PackageRelationship> fournit un moyen rapide et détectable de détection des dépendances et d'ajout d'informations associées à tout ou partie du package.  
  
<a name="Dependency_Relationships"></a>   
##### Relations de dépendance  
 Les relations de dépendance sont utilisées pour décrire les dépendances qu'une partie crée sur d'autres parties.  Par exemple, un package peut contenir une partie HTML comprenant une ou plusieurs balises d'image \<img\>.  Les balises d'image font référence à des images situées sur d'autres parties internes ou externes au package \(comme étant accessibles sur Internet\).  La création d'une <xref:System.IO.Packaging.PackageRelationship> associée avec un fichier HTML accélère et facilite la découverte et l'accès des ressources dépendantes.  Une application de navigation ou de visionnage peut accéder directement aux relations de parties et commencer immédiatement l'assemblage des ressources dépendantes sans connaître le schéma ou analyser le document.  
  
<a name="Information_Relationships"></a>   
##### Relations d'informations  
 Similaire à une note ou annotation, une <xref:System.IO.Packaging.PackageRelationship> peut également être utilisée pour stocker d'autres types d'informations à associer à une partie, sans avoir besoin de réellement modifier le contenu de la partie même.  
  
<a name="XPS_Documents"></a>   
## Documents XPS  
 Un document [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] est un package qui contient un ou plusieurs documents fixes avec toutes les ressources et informations nécessaires pour le rendu.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] est également le format de fichier de spoule d'impression [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] natif.  Un <xref:System.Windows.Xps.Packaging.XpsDocument> est stocké dans le dataset ZIP standard et peut comprendre une combinaison de composants XML et binaires, tels que des fichiers d'image et de police. Des [PackageRelationships](#PackageRelationships) sont utilisés pour définir les dépendances entre le contenu et les ressources nécessaires pour afficher le document.  La conception du <xref:System.Windows.Xps.Packaging.XpsDocument> offre une solution haute fidélité de document unique prenant en charge plusieurs utilisations :  
  
-   Lecture, écriture et stockage de contenu et de ressources de document fixe en tant que fichier unique, portable et facile à distribuer.  
  
-   Affichage de documents avec l'application de visionneuse [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
-   Copie de documents au format de sortie natif du spoule d'impression de [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  
  
-   Routage direct de documents vers une imprimante compatible avec le format [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
## Voir aussi  
 <xref:System.Windows.Documents.FixedDocument>   
 <xref:System.Windows.Documents.FlowDocument>   
 <xref:System.Windows.Xps.Packaging.XpsDocument>   
 <xref:System.IO.Packaging.ZipPackage>   
 <xref:System.IO.Packaging.ZipPackagePart>   
 <xref:System.IO.Packaging.PackageRelationship>   
 <xref:System.Windows.Controls.DocumentViewer>   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Vue d'ensemble des documents dynamiques](../../../../docs/framework/wpf/advanced/flow-document-overview.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Sérialisation et stockage de documents](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)