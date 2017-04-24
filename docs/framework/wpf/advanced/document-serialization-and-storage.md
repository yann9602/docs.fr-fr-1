---
title: "S&#233;rialisation et stockage de documents | Microsoft Docs"
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
  - "documents, sérialisation"
  - "documents, storage"
  - "sérialisation de documents"
  - "stockage de documents"
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# S&#233;rialisation et stockage de documents
[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] fournit un environnement puissant pour créer et afficher des documents de haute qualité.  Grâce à des fonctionnalités améliorées prenant en charge les documents fixes comme les documents dynamiques, des contrôles d'affichage avancés et des fonctions graphiques 2D et 3D puissantes, les applications [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] offrent un niveau de qualité et une expérience utilisateur inégalés.  La possibilité de gérer une représentation en mémoire d'un document de manière flexible est une fonctionnalité clé de [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] ; en outre, la quasi\-totalité des applications requièrent de pouvoir enregistrer et charger efficacement des documents d'un magasin de données.  Le processus de conversion d'un document d'une représentation en mémoire interne en un magasin de données externes est nommé [sérialisation](GTMT).  Le processus inverse de lecture d'un magasin de données et de recréation de l'instance en mémoire d'origine est appelé désérialisation.  
  
   
  
<a name="AboutSerialization"></a>   
## À propos de la sérialisation de documents  
 Dans l'idéal, les processus de [sérialisation](GTMT) et de désérialisation d'un document depuis et vers la mémoire sont transparents pour l'application.  L'application appelle une méthode de sérialiseur « en écriture » pour enregistrer le document, tandis qu'une méthode de désérialiseur « en lecture » accède au magasin de données pour recréer l'instance d'origine en mémoire.  Le format spécifique de stockage des données ne concerne généralement pas l'application tant que les processus de sérialisation et de désérialisation recréent le document d'origine.  
  
 Les applications fournissent souvent plusieurs options de sérialisation qui permettent à l'utilisateur d'enregistrer des documents sur différents médias ou sous un format différent.  Par exemple, une application peut proposer des options « Enregistrer sous » pour le stockage d'un document dans un fichier sur disque, une base de données ou un service Web.  De même, différents sérialiseurs peuvent stocker le document sous divers formats, tels que les formats HTML, RTF, XML, XPS ou encore un format tiers.  Pour l'application, la sérialisation définit une interface qui isole les détails du média de stockage dans l'implémentation de chaque sérialiseur spécifique.  Outre les avantages de l'encapsulation des détails de stockage, les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] <xref:System.Windows.Documents.Serialization> offrent également plusieurs autres fonctionnalités importantes.  
  
### Fonctionnalités des sérialiseurs de documents .NET Framework 3.0  
  
-   L'accès direct aux objets de document de niveau supérieur \([arborescence logique](GTMT) et objets visuels\) permet un stockage efficace de contenu paginé, d'éléments 2D\/3D, d'images, de fichiers multimédias, de liens hypertexte, d'annotations et d'autre contenu de média.  
  
-   Fonctionnement [synchrone](GTMT) et [asynchrone](GTMT).  
  
-   Prise en charge de sérialiseurs de plug\-ins avec fonctionnalités améliorées :  
  
    -   Accès à l'échelle du système pour toutes les applications [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] ;  
  
    -   Détectabilité de plug\-ins d'application simplifiée ;  
  
    -   Déploiement, installation et mise à jour simples pour les plug\-ins tiers personnalisés ;  
  
    -   Prise en charge des paramètres et des options d'exécution personnalisés par l'interface utilisateur.  
  
### Chemin d'accès d'impression XPS  
 Le chemin d'impression [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] fournit également un mécanisme extensible pour l'écriture de documents via la sortie d'impression.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] fait office à la fois de format de fichier de document et de spouleur d'impression natif pour [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  Les documents [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] peuvent être envoyés directement aux imprimantes compatibles [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] sans nécessiter de conversion dans un format intermédiaire.  Consultez la rubrique [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md) pour obtenir des informations supplémentaires sur les options et les fonctionnalités de chemin d'impression.  
  
<a name="PluginSerializers"></a>   
## Sérialiseurs de plug\-ins  
 Les API <xref:System.Windows.Documents.Serialization> offrent une prise en charge des sérialiseurs de plug\-ins et des sérialiseurs liés installés séparément de l'application ; elles effectuent une liaison au moment de l'exécution et sont accessibles via le mécanisme de découverte <xref:System.Windows.Documents.Serialization.SerializerProvider>.  Les sérialiseurs de plug\-ins offrent des améliorations considérables pour un déploiement simplifié et une utilisation à l'échelle du système.  Les sérialiseurs liés peuvent également être implémentés pour les environnements de [confiance partielle](GTMT) tels que les [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] dans lesquelles les sérialiseurs de plug\-ins ne sont pas accessibles.  Les sérialiseurs liés, basés sur une implémentation dérivée de la classe <xref:System.Windows.Documents.Serialization.SerializerWriter>, sont compilés et liés directement dans l'application.  Les sérialiseurs de plug\-ins comme les sérialiseurs liés fonctionnent selon des méthodes et des événements publics identiques qui facilitent leur utilisation séparée ou simultanée dans la même application.  
  
 Les sérialiseurs de plug\-ins aident les développeurs d'applications en fournissant une extensibilité aux nouveaux types de stockage et formats de fichiers sans nécessiter de codage direct pour chaque format potentiel au moment de la génération.  Ils représentent également un atout pour les développeurs tiers, qui bénéficient ainsi d'un moyen standardisé pour déployer, installer et mettre à jour les plug\-ins système accessibles pour les formats de fichiers personnalisés ou propriétaires.  
  
### Utilisation d'un sérialiseur de plug\-ins  
 Les sérialiseurs de plug\-ins sont simples à utiliser.  La classe <xref:System.Windows.Documents.Serialization.SerializerProvider> énumère un objet <xref:System.Windows.Documents.Serialization.SerializerDescriptor> pour chaque plug\-in installé sur le système.  La propriété <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> filtre les plug\-ins installés en fonction de la configuration actuelle et vérifie que le sérialiseur peut être chargé et utilisé par l'application.  La classe <xref:System.Windows.Documents.Serialization.SerializerDescriptor> fournit également d'autres propriétés, telles que les propriétés <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> et <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, que l'application peut utiliser afin d'inviter l'utilisateur à sélectionner un sérialiseur pour un format de sortie disponible.  Un sérialiseur de plug\-ins par défaut pour le format [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] est fourni avec [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] et est toujours énuméré.  Une fois le format de sortie sélectionné par l'utilisateur, la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> est utilisée pour créer une classe <xref:System.Windows.Documents.Serialization.SerializerWriter> pour le format spécifique.  La méthode <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> peut alors être appelée pour la sortie du flux de données du document dans le magasin de données.  
  
 L'exemple suivant montre une application qui utilise la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider> dans une propriété « PlugInFileFilter ».  La propriété PlugInFileFilter énumère les plug\-ins installés et génère une chaîne de filtrage avec les options de fichier disponibles pour une classe <xref:Microsoft.Win32.SaveFileDialog>.  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 L'exemple suivant montre comment utiliser la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> pour stocker un document donné dans un format spécifié, une fois le fichier de sortie nommé par l'utilisateur.  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### Installation de sérialiseurs de plug\-ins  
 La classe <xref:System.Windows.Documents.Serialization.SerializerProvider> fournit l'interface d'application de niveau supérieur pour la découverte du sérialiseur de plug\-ins et l'accès à ce dernier.  <xref:System.Windows.Documents.Serialization.SerializerProvider> détecte et fournit à l'application la liste des sérialiseurs installés et accessibles sur le système.  Les caractéristiques des sérialiseurs installés sont définies via les paramètres du Registre.  Les sérialiseurs de plug\-ins peuvent être ajoutés au Registre par la méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> ; si [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] n'est pas encore installé, le script d'installation de plug\-ins peut définir lui\-même directement les valeurs de Registre.  La méthode <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> peut être utilisée pour supprimer un plug\-in installé précédemment, ou un script de désinstallation peut réinitialiser, de manière identique, les paramètres du Registre.  
  
### Création d'un sérialiseur de plug\-ins  
 Les sérialiseurs de plug\-ins et les sérialiseurs liés utilisent les mêmes méthodes et événements publics exposés et sont conçus pour un fonctionnement [synchrone](GTMT) ou [asynchrone](GTMT).  La création d'un sérialiseur de plug\-ins se déroule généralement en trois étapes principales :  
  
1.  La première étape consiste à implémenter et à déboguer le sérialiseur comme sérialiseur lié.  Le fait de créer un sérialiseur compilé et lié directement dans une application test permet d'accéder aux points d'arrêt et autres services de débogage utiles lors du test.  
  
2.  Une fois le sérialiseur intégralement testé, une interface <xref:System.Windows.Documents.Serialization.ISerializerFactory> est ajoutée pour créer un plug\-in.  L'interface <xref:System.Windows.Documents.Serialization.ISerializerFactory> permet un accès total à tous les objets [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)], notamment à l'arborescence logique, aux objets <xref:System.Windows.UIElement>, <xref:System.Windows.Documents.IDocumentPaginatorSource>et aux éléments <xref:System.Windows.Media.Visual>.  En outre, l'interface <xref:System.Windows.Documents.Serialization.ISerializerFactory> fournit les mêmes méthodes et événements synchrones et asynchrones que ceux utilisés par les sérialiseurs liés.  La sortie des documents volumineux pouvant prendre un certain temps, un fonctionnement asynchrone est recommandé de sorte à maintenir la réactivité de l'intervention de l'utilisateur tout en offrant une option « Annuler » en cas de problème avec le magasin de données.  
  
3.  Une fois le sérialiseur de plug\-ins créé, un script d'installation est implémenté pour distribuer et installer \(ou désinstaller\) le plug\-in \(voir la section ci\-dessus intitulée « [Installation de sérialiseurs de plug\-ins](#InstallingPluginSerializers) »\).  
  
## Voir aussi  
 <xref:System.Windows.Documents.Serialization>   
 <xref:System.Windows.Xps.XpsDocumentWriter>   
 <xref:System.Windows.Xps.Packaging.XpsDocument>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [XML Paper Specification : Vue d'ensemble \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=106246)