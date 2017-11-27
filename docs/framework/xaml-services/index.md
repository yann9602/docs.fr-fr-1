---
title: Services XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: b8d1214e011e4a6569b5612d7be93ed05b776166
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-services"></a>Services XAML
Cette rubrique décrit les fonctionnalités d’un ensemble de la technologie appelée Services XAML .NET Framework. La plupart des services et API décrits se trouvent dans l’assembly System.Xaml, qui est un assembly introduite avec la [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ensemble d’assemblys principaux .NET. Les services incluent des lecteurs et writers, les classes du schéma et la prise en charge des schémas, des fabriques, attribution de classes, XAML intrinsèque prise en charge et autres fonctionnalités de langage XAML.  
  
## <a name="about-this-documentation"></a>À propos de cette Documentation  
 Documentation conceptuelle pour les Services XAML .NET Framework part du principe que vous disposez d’expérience avec le langage XAML et comment il peut s’appliquer à une infrastructure spécifique, par exemple [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ou [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)], ou zone, de fonctionnalité d’une technologie spécifique pour exemple de personnalisation de la génération des fonctionnalités dans <xref:Microsoft.Build.Framework.XamlTypes>. Cette documentation ne tente pas d’expliquer les principes de base du langage XAML comme un langage de balisage, la terminologie de syntaxe XAML ou autres introductive. Elle se concentre plutôt sur l’utilisation spécifique les Services XAML .NET Framework qui sont activés dans la bibliothèque de l’assembly System.Xaml. La plupart de ces API est destinées aux scénarios d’extensibilité et intégration du langage XAML. Cela peut inclure les éléments suivants :  
  
-   Extension des capacités de la base lecteurs ou writers XAML (traitement direct du flux de nœud XAML dériver votre propre lecteur XAML ou un writer XAML).  
  
-   Définition des types personnalisés utilisable en XAML qui n’ont pas de dépendances d’infrastructure spécifique et en attribuant les types pour transmettre leur XAML tapez caractéristiques du système pour les Services XAML .NET Framework.  
  
-   Hébergement des lecteurs ou writers XAML en tant que composant d’une application, tel qu’un concepteur visuel ou un éditeur interactif pour les sources de balisage XAML.  
  
-   L’écriture des convertisseurs de valeur XAML (extensions de balisage, les convertisseurs de type pour les types personnalisés).  
  
-   Définition d’un contexte de schéma XAML personnalisé (à l’aide d’autres techniques de chargement d’assemblys pour les sources de type de stockage ; à l’aide de techniques de recherche de types connus au lieu de toujours reflétant les assemblys à l’aide de concepts d’assemblys chargés qui n’utilisent pas le CLR `AppDomain` et son modèle de sécurité associé).  
  
-   Étendre le système de type XAML base.  
  
-   À l’aide de la `Lookup` ou `Invoker` techniques pour influencer le code XAML de type système et l’évaluation des stockages de type.  
  
 Si vous recherchez une partie introductive dans XAML en tant que langage, vous pouvez essayer de [vue d’ensemble du XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Cette rubrique aborde XAML pour un public qui est une nouveauté pour [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] et également à l’aide de balisage XAML et les fonctionnalités de langage XAML. Un autre document utile est la partie introductive dans le [spécification du langage XAML](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>Les Services XAML .NET framework et System.Xaml dans l’Architecture .NET  
 Dans les versions précédentes de [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)], prise en charge des fonctionnalités de langage XAML a été implémentée par des infrastructures qui reposent sur [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] et [!INCLUDE[vsindigo](../../../includes/vsindigo-md.md)]) et par conséquent variées dans son comportement et l’API utilisée en fonction infrastructure spécifique vous utilisiez. Cela inclus le code XAML analyseur et son objet de graphiquement le mécanisme de création, intrinsèques du langage XAML, la prise en charge de la sérialisation et ainsi de suite.  
  
 Dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], les Services XAML .NET Framework et l’assembly System.Xaml définissent la plupart de ce qui est nécessaire pour prendre en charge des fonctionnalités de langage XAML. Cela inclut les classes de base pour les lecteurs et writers XAML. La fonctionnalité la plus importante ajoutée aux Services XAML .NET Framework qui n’était pas présente dans les implémentations XAML spécifiques à l’infrastructure est une représentation de système de type pour XAML. La représentation sous forme de système de type présente le code XAML d’une manière orientée objet qui est centrée sur les fonctions XAML sans définir de dépendances sur des fonctions spécifiques des infrastructures.  
  
 Le système de type XAML n’est pas limité par la forme de balisage ou les caractéristiques d’exécution de l’origine XAML ; ni est limitée par n’importe quel système de type de stockage spécifique. Le système de type XAML inclut des représentations d’objets pour les types, membres, les contextes de schéma XAML, les concepts de niveau XML et autres concepts du langage XAML ou XAML intrinsèques. À l’aide d’ou de l’extension du système de type XAML permet de dériver de classes telles que les lecteurs XAML et les writers XAML et étendre les fonctionnalités de représentations XAML dans des fonctionnalités spécifiques activées par une infrastructure, une technologie ou une application qui consomme ou émet le XAML. Le concept d’un contexte de schéma XAML permet des opérations d’écriture de graphique d’objet pratique à partir de la combinaison d’une implémentation de writer d’objet XAML, système de type de stockage d’une technologie comme communiqués via les informations d’assembly dans le contexte et le nœud XAML source. Pour plus d’informations sur le concept de schéma XAML. consultez [contexte de schéma XAML par défaut et le contexte de schéma XAML WPF](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Flux de nœud XAML, les lecteurs XAML et les Writers XAML  
 Pour comprendre le rôle que joue des Services XAML .NET Framework dans la relation entre le langage XAML et les technologies spécifiques qui utilisent XAML en tant que langage, il est utile de comprendre le concept d’un flux de nœud XAML et la manière qui influe sur l’API et terminologie. Le flux de nœud XAML est un intermédiaire conceptuel entre une représentation de langage XAML et le graphique d’objet qui représente le code XAML ou le définit.  
  
-   Un lecteur XAML est une entité qui traite le XAML sous une forme et génère un flux de nœud XAML. Dans l’API, un lecteur XAML est représenté par la classe de base <xref:System.Xaml.XamlReader>.  
  
-   Un writer XAML est une entité qui traite un flux de nœud XAML et qui produit quelque chose d’autre. Dans l’API, un writer XAML est représenté par la classe de base <xref:System.Xaml.XamlWriter>.  
  
 Les deux scénarios courants impliquant XAML sont le chargement XAML pour instancier un graphique d’objet et l’enregistrement d’un graphique d’objet à partir d’une application ou un outil et produisant une représentation XAML (généralement en forme de balisage enregistré en tant que fichier texte). Chargement de XAML et la création d’un graphique d’objet sont souvent appelée dans cette documentation en tant que le chemin de chargement. L’enregistrement ou la sérialisation d’un graphique d’objets existant en XAML est souvent appelée dans cette documentation comme chemin d’accès.  
  
 Le type le plus courant de chemin de chargement peut être décrite comme suit :  
  
-   Commencez par une représentation XAML, dans le format XML encodé en UTF et enregistrée dans un fichier texte.  
  
-   Chargez ce XAML dans <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader>est un <xref:System.Xaml.XamlReader> sous-classe.  
  
-   Le résultat est un flux de nœud XAML. Vous pouvez accéder à des nœuds individuels du flux de nœud XAML à l’aide <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> API. L’opération la plus classique ici consiste à avancer dans le flux de nœud XAML, le traitement de chaque nœud à l’aide d’un « enregistrement en cours » métaphore.  
  
-   Passez les nœuds obtenus à partir du flux de nœud XAML pour un <xref:System.Xaml.XamlObjectWriter> API. <xref:System.Xaml.XamlObjectWriter>est un <xref:System.Xaml.XamlWriter> sous-classe.  
  
-   Le <xref:System.Xaml.XamlObjectWriter> écrit un graphique d’objet, un objet à la fois, conformément à sa progression via le flux de nœud XAML source. Pour cela, à l’aide d’un contexte de schéma XAML et l’implémentation qui peut accéder aux assemblys et les types d’un système de type de stockage et le framework.  
  
-   Appelez <xref:System.Xaml.XamlObjectWriter.Result%2A> à la fin du flux de nœud XAML pour obtenir l’objet racine du graphique d’objets.  
  
 Le type le plus courant de chemin d’enregistrement peut être décrite comme suit :  
  
-   Démarrer avec le graphique d’objet d’une heure d’exécution de toute application, le contenu de l’interface utilisateur et l’état d’une durée d’exécution, ou un plus petit segment de la représentation d’objet d’une application globale au moment de l’exécution.  
  
-   À partir d’un objet de début logique, tels qu’une racine de l’application ou la racine du document, chargez les objets dans <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader>est un <xref:System.Xaml.XamlReader> sous-classe.  
  
-   Le résultat est un flux de nœud XAML. Vous pouvez accéder à des nœuds individuels du flux de nœud XAML à l’aide <xref:System.Xaml.XamlObjectReader> et <xref:System.Xaml.XamlReader> API. L’opération la plus classique ici consiste à avancer dans le flux de nœud XAML, le traitement de chaque nœud à l’aide d’un « enregistrement en cours » métaphore.  
  
-   Passez les nœuds obtenus à partir du flux de nœud XAML pour un <xref:System.Xaml.XamlXmlWriter> API. <xref:System.Xaml.XamlXmlWriter>est un <xref:System.Xaml.XamlWriter> sous-classe.  
  
-   Le <xref:System.Xaml.XamlXmlWriter> écrit du code XAML dans un UTF XML encodage. Vous pouvez l’enregistrer comme un fichier texte, en tant que flux, ou dans d’autres écrans.  
  
-   Appelez <xref:System.Xaml.XamlXmlWriter.Flush%2A> pour obtenir la sortie finale.  
  
 Pour plus d’informations sur les concepts de flux de nœud XAML, consultez [Concepts et Structures du flux de nœud XAML compréhension](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>Classe XamlServices  
 Il n’est pas toujours nécessaire de traiter un flux de nœud XAML. Si vous souhaitez un chemin de chargement de base ou un chemin d’enregistrement de base, vous pouvez utiliser des API dans le <xref:System.Xaml.XamlServices> classe.  
  
-   Diverses signatures de <xref:System.Xaml.XamlServices.Load%2A> implémentent un chemin de chargement. Vous pouvez charger un fichier ou un flux, ou encore un <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> ou <xref:System.Xaml.XamlReader> dans un wrapper votre entrée XAML en procédant au chargement avec les API de ce lecteur.  
  
-   Diverses signatures de <xref:System.Xaml.XamlServices.Save%2A> enregistrer un graphique d’objets et génère un résultat sous forme de flux, fichier, ou <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instance.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A>convertit XAML en liant un chemin de chargement et l’enregistrer en tant que d’une seule opération. Un contexte de schéma ou un système de type de stockage différent peut être utilisé pour <xref:System.Xaml.XamlReader> et <xref:System.Xaml.XamlWriter>, qui est l’élément qui influence le mode de transformation du code XAML obtenu.  
  
 Pour plus d’informations sur l’utilisation de <xref:System.Xaml.XamlServices>, consultez [classe XAMLServices et lecture de XAML de base ou l’écriture](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>Système de Type XAML  
 Le système de type XAML fournit les API requises pour fonctionner avec un nœud individuel donné d’un flux de nœud XAML.  
  
 <xref:System.Xaml.XamlType>est la représentation sous forme d’un objet - ce que vous traitez entre un nœud objet de début et un nœud d’objet de fin.  
  
 <xref:System.Xaml.XamlMember>est la représentation sous forme d’un membre d’un objet - ce que vous traitez entre un nœud membre de début et un nœud membre de fin.  
  
 API telles que <xref:System.Xaml.XamlType.GetAllMembers%2A> et <xref:System.Xaml.XamlType.GetMember%2A> et <xref:System.Xaml.XamlMember.DeclaringType%2A> signalent les relations entre un <xref:System.Xaml.XamlType> et <xref:System.Xaml.XamlMember>.  
  
 Le comportement par défaut du système de type XAML comme implémenté par les Services XAML .NET Framework est basé sur le common language runtime (CLR) et analyse statique des types CLR dans les assemblys en utilisant la réflexion. Par conséquent, pour un type CLR spécifique, l’implémentation par défaut du système de type XAML peut exposer le schéma XAML de ce type et ses membres et le signaler en termes de système de type XAML. Dans le système de type XAML par défaut, le concept d’assignabilité de types est mappé à l’héritage du CLR et les concepts des instances, types valeur et ainsi de suite sont également mappés aux comportements et les fonctionnalités du CLR prise en charge.  
  
## <a name="reference-for-xaml-language-features"></a>Référence les fonctionnalités du langage XAML  
 Pour prendre en charge XAML, les Services XAML .NET Framework fournit une implémentation spécifique des concepts du langage XAML tel que défini pour l’espace de noms XAML du langage XAML. Ces résultats sont décrits comme des pages de référence spécifique. Les fonctionnalités de langage sont documentées dans la perspective de la façon dont elles se comportent lorsqu’ils sont traités par un lecteur ou un writer XAML défini par les Services XAML .NET Framework. Pour plus d'informations, consultez [XAML Namespace (x:) Language Features](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).
