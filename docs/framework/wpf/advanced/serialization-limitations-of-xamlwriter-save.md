---
title: "Limitations de s&#233;rialisation de XamlWriter.Save | Microsoft Docs"
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
  - "limitations de XamlWriter.Save"
  - "limitations de sérialisation de XamlWriter.Save"
  - "XamlWriter.Save, limitations de sérialisation de"
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Limitations de s&#233;rialisation de XamlWriter.Save
L'[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> peut être utilisée pour sérialiser le contenu d'une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] en tant que fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Cependant, il existe quelques limitations notables concernant ce qui est exactement sérialisé.  Ces limitations, ainsi que des considérations générales, sont documentées dans cette rubrique.  
  
   
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## Représentation au moment de l'exécution, non au moment du design  
 La philosophie de base concernant ce qui est sérialisé par un appel à <xref:System.Windows.Markup.XamlWriter.Save%2A> est que le résultat sera une représentation de l'objet sérialisé, au moment de l'exécution.  De nombreuses propriétés au moment du design qui sont dans le fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d'origine peuvent être déjà optimisées ou perdues au moment où [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est chargé sous forme d'objets en mémoire, et ne sont pas conservées lorsque vous appelez <xref:System.Windows.Markup.XamlWriter.Save%2A> pour effectuer la sérialisation.  Le résultat sérialisé est une représentation effective de l'arborescence logique construite de l'application, mais pas nécessairement du [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d'origine qui l'a produite.  Ces questions rendent extrêmement difficile l'utilisation de la sérialisation <xref:System.Windows.Markup.XamlWriter.Save%2A> dans le cadre d'une aire de conception [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] importante.  
  
<a name="Serialization_is_Self_Contained"></a>   
## La sérialisation est autonome  
 La sortie sérialisée de <xref:System.Windows.Markup.XamlWriter.Save%2A> est autonome, tout ce qui est sérialisé est contenu à l'intérieur d'une seule page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], avec un seul élément racine, et sans références externes autres que des [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].  Par exemple, si votre page référençait des ressources en provenance de ressources d'une application, elles apparaîtront comme si elles étaient un composant de la page sérialisée.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## Les références d'extension sont déréférencées  
 Des références communes à des objets réalisés dans divers formats d'extension de balisage, tels que `StaticResource` ou `Binding`, seront déréférencées par le processus de sérialisation.  Elles étaient déjà déréférencées au moment où les objets en mémoire étaient créés par l'exécution de l'application, et la logique de <xref:System.Windows.Markup.XamlWriter.Save%2A> ne revisite pas le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] d'origine pour restaurer de telles références dans la sortie sérialisée.  Ceci fige potentiellement toute valeur liée aux données ou obtenue depuis une ressource à la dernière valeur utilisée par la représentation au moment de l'exécution, avec uniquement une capacité limitée ou indirecte de distinguer une telle valeur d'une autre quelconque valeur définie localement.  Les images sont aussi sérialisées comme des références d'objet vers des images telles qu'elles existent dans le projet, plutôt que comme des références sources d'origine, perdant tout fichier ou [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] qui était référencé à l'origine.  Même les ressources déclarées au sein de la même page sont sérialisées au point où elles étaient référencées, et non conservées en tant que clé de collection de ressources.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## La gestion d'événements n'est pas conservée  
 Lorsque des gestionnaires d'événements ajoutés via [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont sérialisés, ils ne sont pas conservés.  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sans code\-behind \(et également sans le mécanisme x:Code associé\) n'a aucun moyen de sérialiser la logique procédurale au moment de l'exécution.  La sérialisation étant autonome et limitée à l'arborescence logique, il n'existe pas de fonction pour le stockage des gestionnaires d'événements.  En conséquence, les attributs du gestionnaire d'événements, l'attribut lui\-même ainsi que la valeur de chaîne qui nomme le gestionnaire, sont supprimés de la sortie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## Scénarios réalistes d'utilisation de XAMLWriter.Save  
 Si les limitations énumérées ici sont importantes, il reste toutefois plusieurs scénarios appropriés pour l'utilisation de <xref:System.Windows.Markup.XamlWriter.Save%2A> à des fins de sérialisation.  
  
-   Sortie vecteur ou graphique : la sortie de la zone rendue peut être utilisée pour reproduire les mêmes vecteurs ou graphiques au moment du rechargement.  
  
-   Texte au format RTF et documents dynamiques : le texte, ainsi que tous les éléments de formatage et la relation contenant\-contenu de l'élément situé à l'intérieur, sont conservés dans la sortie.  Ceci peut être utile pour les mécanismes se rapprochant de la fonctionnalité de presse\-papiers.  
  
-   Conservation des données des objets métier : si vous avez stocké des données dans des éléments personnalisés, telles que des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], tant que vos objets métier suivent les règles de base de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] comme la fourniture de constructeurs personnalisés et la conversion pour les valeurs de propriétés par référence, ces objets métier peuvent être perpétués au moyen de la sérialisation.