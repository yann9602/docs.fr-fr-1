---
title: "Code-behind et XAML dans WPF | Microsoft Docs"
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
  - "fichiers code-behind, XAML"
  - "XAML, code-behind"
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Code-behind et XAML dans WPF
<a name="introduction"></a> Code\-behind est un terme utilisé pour décrire le code joint avec les objets définis par balisage, lorsqu'une page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est compilée par balisage.  Cette rubrique explique les exigences liées au code\-behind et décrit un mécanisme alternatif de code incorporé pour le code en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Composants requis](#Prerequisites)  
  
-   [Code\-behind et langage XAML](#codebehind_and_the_xaml_language)  
  
-   [Exigences concernant le code\-behind, le gestionnaire d'événements et les classes partielles dans WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x:Code](#x_Code)  
  
-   [Limitations liées au code incorporé](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## Composants requis  
 Cette rubrique part du principe que vous avez lu [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) et possédez des connaissances de base de [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et de la programmation orientée objet.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## Code\-behind et langage XAML  
 Le langage XAML inclut des fonctionnalités de niveau de langage qui permettent d'associer des fichiers de code aux fichiers de balisage, du côté du fichier de balisage.  Spécifiquement, le langage XAML définit les fonctionnalités de langage [x:Class, directive](../../../../docs/framework/xaml-services/x-class-directive.md), [x:Subclass, directive](../../../../docs/framework/xaml-services/x-subclass-directive.md) et [x:ClassModifier, directive](../../../../docs/framework/xaml-services/x-classmodifier-directive.md).  En revanche, le langage XAML ne spécifie pas comment le code doit être produit et comment intégrer le balisage et le code.  C'est aux infrastructures telles que WPF que revient de déterminer comment intégrer le code, comment utiliser XAML dans l'application et les modèles de programmation, et les actions de génération ou les autres supports requis.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## Exigences concernant le code\-behind, le gestionnaire d'événements et les classes partielles dans WPF  
  
-   La classe partielle doit dériver du type de la classe qui stocke l'élément racine.  
  
-   Notez que, du côté du code\-behind, avec le comportement par défaut des actions de génération de compilation du balisage, vous pouvez laisser l'espace de dérivation dans la définition de classe partielle.  Le résultat compilé supposera que le type de stockage de la racine de page sera la base de la classe partielle, même s'il n'est pas spécifié.  Toutefois, compter sur ce comportement n'est pas une meilleure pratique.  
  
-   Les gestionnaires d'événements que vous écrivez dans le code\-behind doivent être des méthodes d'instance et ne peuvent pas être des méthodes statiques.  Ces méthodes doivent être définies par la classe partielle dans l'espace de noms CLR identifié par `x:Class`.  Vous ne pouvez pas qualifier le nom d'un gestionnaire d'événements pour demander à un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de rechercher un gestionnaire d'événements en vue de la transmission des événements dans une portée de classe différente.  
  
-   Le gestionnaire doit correspondre au délégué pour l'événement approprié dans le système de types de stockage.  
  
-   De manière spécifique, pour le langage [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)], vous pouvez utiliser le mot clé `Handles` spécifique au langage pour associer des gestionnaires à des instances et des événements dans la déclaration de gestionnaire, au lieu de joindre des gestionnaires avec des attributs en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Cette technique présente toutefois certaines limitations car le mot clé `Handles` ne peut pas prendre en charge toutes les fonctionnalités spécifiques du système d'événements [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tel que certains scénarios d'événements routés ou événements attachés.  Pour plus d'informations, consultez [Gestion des événements Visual Basic et WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## x:Code  
 [x:Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) est un élément directeur défini dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Un élément de directive `x:Code` peut contenir un code de programmation incorporé.  Le code défini en ligne peut interagir avec le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sur la même page.  L'exemple suivant illustre le code [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] incorporé.  Notez que le code est à l'intérieur de l'élément `x:Code` et qu'il doit être entouré par `<CDATA[`...`]]>` pour se soustraire au contenu de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], de manière à ce qu'un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] \(interprétant le schéma [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \) n'essaie pas d'interpréter le contenu littéralement en tant que code [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## Limitations liées au code incorporé  
 Évitez ou limitez l'utilisation de code inline.  En termes d'architecture et de philosophie du codage, la séparation entre balise et code\-behind permet d'attribuer des rôles bien distincts au concepteur et au développeur.  À un niveau plus technique, le code que vous écrivez pour le code inline peut être plus difficile à écrire, parce que vous écrivez toujours dans la classe partielle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] générée et que vous pouvez uniquement utiliser les mappages d'espaces de noms XML par défaut.  Comme vous ne pouvez pas ajouter d'instructions `using`, vous devez qualifier entièrement la plupart des appels [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] que vous faites.  Les mappages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut incluent la plupart mais pas tous les espaces de noms [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] qui sont présents dans les assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ; vous devrez qualifier pleinement des appels aux types et aux membres contenus dans les autres espaces de noms CLR.  Vous ne pouvez rien définir non plus au\-delà de la classe partielle dans le code inline, et toutes les entités de code utilisateur que vous référencez doivent exister en tant que membre ou variable dans la classe partielle générée.  Enfin, d'autres fonctionnalités de programmation spécifiques au langage, telles que les macros ou `#ifdef` pour les variables globales ou les variables de génération, ne sont pas disponibles.  Pour plus d'informations, consultez [x:Code, type XAML intrinsèque](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md).  
  
## Voir aussi  
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [x:Code, type XAML intrinsèque](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)   
 [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)