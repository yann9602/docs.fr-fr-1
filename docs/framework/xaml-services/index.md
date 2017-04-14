---
title: "XAML Services | Microsoft Docs"
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
  - "XAML [XAML Services], System.Xaml concepts"
  - "XAML Services in WPF [XAML Services]"
  - "System.Xaml [XAML Services], conceptual documentation"
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: 13
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 13
---
# XAML Services
Cette rubrique décrit les fonctions d'un ensemble de technologies appelé services XAML .NET Framework.  La majorité des services et API décrits se trouvent dans l'assembly System.Xaml, qui a été introduit avec le jeu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] des assemblys principaux .NET.  Les services incluent des lecteurs et des writers, des classes de schéma et la prise en charge des schémas, des fabriques, l'affectation d'attributs aux classes, la prise en charge des intrinsèques du langage XAML, ainsi que d'autres fonctionnalités de ce langage.  
  
## À propos de cette documentation  
 La documentation conceptuelle des services XAML .NET Framework part du principe que vous connaissez déjà le langage XAML et la façon dont il peut s'appliquer à une infrastructure spécifique \(par exemple, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ou [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]\) ou à des fonctionnalités technologiques particulières \(par exemple, les fonctionnalités de personnalisation de build de <xref:Microsoft.Build.Framework.XamlTypes>\).  Cette documentation ne tente pas d'expliquer les concepts fondamentaux du XAML en tant que langage de balisage, terminologie de syntaxe XAML ou tout autre contenu introductif.  Elle se concentre plutôt sur l'utilisation spécifique des services XAML .NET Framework qui sont activés dans la bibliothèque d'assemblys System.Xaml.  La plupart de ces API sont pour des scénarios d'intégration et d'extensibilité du langage XAML.  Il peut s'agir de l'un des scénarios suivants :  
  
-   Extension des fonctions des readers ou writers XAML de base \(traitement direct du flux de nœud XAML ou dérivation de votre propre lecteur ou writer XAML\).  
  
-   Définition de types personnalisés utilisables en XAML, qui n'ont pas de dépendances d'infrastructure spécifiques, et association d'attributs à ces types de façon à transmettre leurs caractéristiques de système de type XAML aux services XAML .NET Framework.  
  
-   Hébergement des lecteurs ou writers XAML en tant que composant d'une application \(par exemple, concepteur visuel ou éditeur interactif pour les sources de balisage XAML\).  
  
-   Écriture des convertisseurs de valeurs XAML \(extensions de balisage, convertisseurs de types associés aux types personnalisés\).  
  
-   Définition d'un contexte de schéma XAML personnalisé \(à l'aide d'autres techniques de chargement d'assemblys pour les sources de type de stockage, de techniques de recherche de types connus au lieu de refléter toujours des assemblys, de concepts d'assemblys chargés qui n'utilisent pas le `AppDomain` du CLR et le modèle de sécurité associé\).  
  
-   Extension du système de type XAML de base.  
  
-   Utilisation des techniques `Lookup` ou `Invoker` de façon à influencer le système de type XAML et l'évaluation des stockages de type.  
  
 Si vous recherchez une partie introductive dans XAML en tant que langage, vous pouvez essayer [Vue d'ensemble du langage XAML \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  Cette rubrique aborde XAML pour un public non familier de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], ni de l'utilisation des fonctionnalités de balisage XAML et de langage XAML.  Un autre document utile est la partie introductive du document [Spécifications du langage XAML \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## Services XAML .NET Framework et System.Xaml dans l'architecture .NET  
 Dans les versions antérieures de [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)], la prise en charge des fonctionnalités du langage XAML a été implémentée par des infrastructures qui reposent sur [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)]\([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] et [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)]\) ; par conséquent, son comportement et l'API utilisée varient en fonction de l'infrastructure spécifique employée.  Celle\-ci inclut l'analyseur XAML et le mécanisme de création de graphique d'objet associé, les intrinsèques du langage XAML, la prise en charge de la sérialisation, etc.  
  
 Dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], les services XAML .NET Framework et l'assembly System.Xaml définissent la plupart des éléments nécessaires à la prise en charge des fonctionnalités du langage XAML.  Cela inclut des classes de base pour les lecteurs XAML et les writers XAML.  La fonctionnalité la plus importante ajoutée aux services XAML .NET Framework qui n'était pas présente dans les implémentations XAML spécifiques à l'infrastructure est une représentation du système de type pour XAML.  La représentation du système de type présente le code XAML selon une représentation orientée objet qui est centrée sur les fonctions XAML sans définir de dépendances sur des fonctions spécifiques des infrastructures.  
  
 Le système de type XAML n'est pas limité par le format de balisage ou les informations d'exécution de l'origine du XAML, ni par un système de types de stockage spécifique.  Le système de type XAML inclut des représentations d'objets pour les types, les membres, les contextes de schéma XAML, les concepts de niveau XML et d'autres concepts ou intrinsèques du langage XAML.  L'utilisation ou l'extension du système de type XAML permet de dériver de classes telles que des lecteurs XAML et des writers XAML, de même que d'étendre les fonctionnalités de représentations XAML dans des fonctionnalités spécifiques activées par une infrastructure, une technologie ou une application qui consomme ou émet du XAML.  Le concept d'un contexte de schéma XAML permet d'effectuer des opérations d'écriture de graphique d'objet pratiques à partir de la combinaison d'une implémentation de writer d'objet XAML, du système de types de stockage d'une technologie tel qu'il est communiqué via les informations d'assembly dans le contexte et de la source de nœud XAML.  Pour plus d'informations sur le concept de schéma XAML.  Consultez [Default XAML Schema Context and WPF XAML Schema Context](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## Flux de nœud XAML, lecteurs XAML et writers XAML  
 Pour comprendre le rôle que les services XAML .NET Framework jouent dans la relation entre le langage XAML et les technologies spécifiques qui emploient XAML en tant que langage, il est utile de cerner le concept de flux de nœud XAML et la manière dont il influe sur l'API et la terminologie.  Le flux de nœud XAML est un intermédiaire conceptuel entre une représentation de langage XAML et le graphique d'objets que le XAML représente ou définit.  
  
-   Un lecteur XAML est une entité qui traite XAML dans une certaine forme et qui génère un flux de nœud XAML.  Dans l'API, il est représenté par la classe de base <xref:System.Xaml.XamlReader>.  
  
-   Un writer XAML est une entité qui traite un flux de nœud XAML et qui génère d'autres éléments.  Dans l'API, il est représenté par la classe de base <xref:System.Xaml.XamlWriter>.  
  
 Les deux scénarios les plus courants impliquant XAML le chargent pour instancier un graphique d'objets, ainsi qu'enregistrer un graphique d'objets à partir d'une application ou d'un outil et générer une représentation XAML \(en général, dans le format de balisage enregistré en tant que fichier texte\).  Dans cette documentation, le chargement de XAML et la création d'un graphique d'objets sont souvent désignés comme étant le chemin de chargement.  Dans cette documentation, l'enregistrement ou la sérialisation d'un graphique d'objets existant en XAML est souvent désigné comme étant le chemin d'enregistrement.  
  
 Le type de chemin de chargement le plus courant peut être décrit comme suit :  
  
-   Commencez par une représentation XAML, au format XML encodé par UTF et enregistrée en tant que fichier texte.  
  
-   Chargez ce XAML dans <xref:System.Xaml.XamlXmlReader>.  <xref:System.Xaml.XamlXmlReader> est une sous\-classe <xref:System.Xaml.XamlReader>.  
  
-   Le résultat est un flux de nœud XAML.  Vous pouvez accéder à chaque nœud du flux de nœud XAML à l'aide de l'API <xref:System.Xaml.XamlXmlReader> \/ <xref:System.Xaml.XamlReader>.  Dans ce cas, l'opération la plus classique consiste à progresser au sein du flux de nœud XAML, en traitant chaque nœud à l'aide d'une métaphore d'« enregistrement actif ».  
  
-   Passez les nœuds obtenus entre le flux de nœud XAML et une API <xref:System.Xaml.XamlObjectWriter>.  <xref:System.Xaml.XamlObjectWriter> est une sous\-classe <xref:System.Xaml.XamlWriter>.  
  
-   <xref:System.Xaml.XamlObjectWriter> écrit un graphique d'objets \(un objet à la fois\) conformément à la progression au sein du flux de nœud XAML source.  Cela s'effectue à l'aide d'un contexte de schéma XAML et d'une implémentation qui peuvent accéder aux assemblys et aux types d'une infrastructure et d'un système de types de stockage.  
  
-   Appelez <xref:System.Xaml.XamlObjectWriter.Result%2A> à la fin du flux de nœud XAML pour obtenir l'objet racine du graphique d'objet.  
  
 Le type de chemin d'enregistrement le plus courant peut être décrit comme suit :  
  
-   Commencez par le graphique d'objets de l'exécution d'une application entière, le contenu de l'interface utilisateur et l'état d'une exécution, ou par un plus petit segment de la représentation d'objet d'une application globale lors de l'exécution.  
  
-   À partir d'un objet de démarrage logique, tel que la racine d'une application ou la racine d'un document, chargez les objets dans <xref:System.Xaml.XamlObjectReader>.  <xref:System.Xaml.XamlObjectReader> est une sous\-classe <xref:System.Xaml.XamlReader>.  
  
-   Le résultat est un flux de nœud XAML.  Vous pouvez accéder à chaque nœud du flux de nœud XAML à l'aide de l'API <xref:System.Xaml.XamlObjectReader> et <xref:System.Xaml.XamlReader>.  Dans ce cas, l'opération la plus classique consiste à progresser au sein du flux de nœud XAML, en traitant chaque nœud à l'aide d'une métaphore d'« enregistrement actif ».  
  
-   Passez les nœuds obtenus entre le flux de nœud XAML et une API <xref:System.Xaml.XamlXmlWriter>.  <xref:System.Xaml.XamlXmlWriter> est une sous\-classe <xref:System.Xaml.XamlWriter>.  
  
-   <xref:System.Xaml.XamlXmlWriter> écrit du code XAML dans un encodage UTF XML.  Vous pouvez l'enregistrer en tant que fichier texte, flux ou toute autre forme.  
  
-   Appelez <xref:System.Xaml.XamlXmlWriter.Flush%2A> pour obtenir la sortie finale.  
  
 Pour plus d'informations sur les concepts du flux de données du nœud XAML, consultez [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### Classe XamlServices  
 Il n'est pas toujours nécessaire d'utiliser un flux de nœud XAML.  Si vous souhaitez un chemin de chargement de base ou un chemin d'enregistrement de base, vous pouvez utiliser des API dans la classe <xref:System.Xaml.XamlServices>.  
  
-   Diverses signatures de <xref:System.Xaml.XamlServices.Load%2A> implémentent un chemin de chargement.  Vous pouvez charger un fichier, un flux ou encore un <xref:System.Xml.XmlReader>, un <xref:System.IO.TextReader> ou un <xref:System.Xaml.XamlReader> qui incluent dans un wrapper votre entrée XAML en se chargeant avec les API de ce lecteur.  
  
-   Diverses signatures de <xref:System.Xaml.XamlServices.Save%2A> enregistrent un graphique d'objets et génère un résultat sous la forme d'un flux, d'un fichier ou d'une instance <xref:System.Xml.XmlWriter>\/<xref:System.IO.TextWriter>.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> convertit XAML en liant un chemin de chargement et un chemin d'enregistrement comme une seule opération.  Un contexte de schéma ou un système de types de stockage différent peut être utilisé pour <xref:System.Xaml.XamlReader> et <xref:System.Xaml.XamlWriter>, ce qui est l'élément qui influence le mode de transformation du XAML obtenu.  
  
 Pour plus d'informations sur l'utilisation de <xref:System.Xaml.XamlServices>, consultez [XAMLServices Class and Basic XAML Reading or Writing](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## Système de type XAML  
 Le système de type XAML fournit les API requises pour utiliser un nœud individuel donné d'un flux de nœud XAML.  
  
 <xref:System.Xaml.XamlType> est la représentation d'un objet, c'est\-à\-dire ce que vous traitez entre un nœud d'objet de début et un nœud d'objet de fin.  
  
 <xref:System.Xaml.XamlMember> est la représentation d'un membre d'objet, c'est\-à\-dire ce que vous traitez entre un nœud membre de début et un nœud membre de fin.  
  
 Des API telles que <xref:System.Xaml.XamlType.GetAllMembers%2A>, <xref:System.Xaml.XamlType.GetMember%2A> et <xref:System.Xaml.XamlMember.DeclaringType%2A> signalent les relations entre un <xref:System.Xaml.XamlType> et un <xref:System.Xaml.XamlMember>.  
  
 Le comportement par défaut du système de type XAML, tel qu'il est implémenté par les services XAML .NET Framework, repose sur le Common Language Runtime \(CLR\) et sur l'analyse statique des types CLR dans les assemblys par le biais de la réflexion.  Par conséquent, pour un type CLR spécifique, l'implémentation par défaut du système de type XAML peut exposer le schéma XAML de ce type et ses membres, de même que le signaler en termes de système de type XAML.  Dans le système de type XAML par défaut, le concept d'assignabilité de types est mappé à l'héritage CLR. De plus, les concepts d'instances, de types valeur, etc. sont également mappés aux comportements et aux fonctionnalités de prise en charge du CLR.  
  
## Référence pour les fonctionnalités du langage XAML  
 Pour prendre en charge XAML, les services XAML .NET Framework fournissent une implémentation spécifique des concepts du langage XAML, tels qu'ils sont définis pour l'espace de noms XAML de ce langage.  Ceux\-ci sont documentés dans des pages de référence spécifiques.  Les fonctionnalités du langage sont documentées en tenant compte de la façon dont elles se comportent lorsqu'elles sont traitées par un lecteur ou un writer XAML défini par les services XAML .NET Framework.  Pour plus d'informations, consultez [XAML Namespace \(x:\) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).