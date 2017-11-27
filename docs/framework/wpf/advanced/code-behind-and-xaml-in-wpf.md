---
title: Code-behind et XAML dans WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 241fe815f1a7c2e70a664068a47d511a3dbd7e0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="code-behind-and-xaml-in-wpf"></a>Code-behind et XAML dans WPF
<a name="introduction"></a>Code-behind est un terme utilisé pour décrire le code joint avec les objets définis par balisage, lorsqu’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page est compilé par balisage. Cette rubrique décrit la configuration requise pour le code-behind ainsi qu’un mécanisme de code inline d’autre code dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Cette rubrique contient les sections suivantes :  
  
-   [Composants requis](#Prerequisites)  
  
-   [Code-Behind et le langage XAML](#codebehind_and_the_xaml_language)  
  
-   [Code-behind, gestionnaire d’événements et les exigences de classe partielle dans WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x : Code](#x_Code)  
  
-   [Limitations de Code inline](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Cette rubrique suppose que vous avez lu la [vue d’ensemble du XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) et avoir des connaissances de base de la [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et une programmation orientée objet.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Code-Behind et le langage XAML  
 Le langage XAML inclut des fonctionnalités au niveau du langage qui la rendent possible d’associer les fichiers de code avec des fichiers de balisage, du côté du fichier de balisage. Plus précisément, le langage XAML définit les fonctionnalités de langage [x : Class Directive](../../../../docs/framework/xaml-services/x-class-directive.md), [x : Subclass Directive](../../../../docs/framework/xaml-services/x-subclass-directive.md), et [x : ClassModifier Directive](../../../../docs/framework/xaml-services/x-classmodifier-directive.md). Exactement comment le code doit être produit et comment intégrer le balisage et le code ne fait pas partie de ce qui spécifie le langage XAML. Il est de laisser les infrastructures telles que WPF pour déterminer comment intégrer du code, comment pour utiliser XAML dans l’application et de modèles de programmation et de la build actions ou autres prennent en charge que tout cela requiert.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Code-behind, gestionnaire d’événements et les exigences de classe partielle dans WPF  
  
-   La classe partielle doit dériver du type qui stocke l’élément racine.  
  
-   Notez que sous le comportement par défaut des actions de génération de compilation de balisage, vous pouvez laisser la dérivation vide dans la définition de classe partielle sur le côté du code-behind. Le résultat compilé supposera type de sauvegarde de la racine de la page pour servir de base à la classe partielle, même si elle pas spécifiée. Toutefois, la partie de confiance sur ce comportement n’est pas une meilleure pratique.  
  
-   Les gestionnaires d’événements que vous écrivez dans le code-behind doivent être des méthodes d’instance et ne peut pas être des méthodes statiques. Ces méthodes doivent être définies par la classe partielle dans l’espace de noms CLR identifié par `x:Class`. Vous ne pouvez pas qualifier le nom d’un gestionnaire d’événements pour demander à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur à rechercher un gestionnaire d’événements pour la connexion de l’événement dans une portée de classe différente.  
  
-   Le gestionnaire doit correspondre au délégué de l’événement approprié dans le système de type de stockage.  
  
-   Pour le [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] langage en particulier, vous pouvez utiliser spécifique au langage `Handles` mot clé pour associer des gestionnaires à des instances et des événements dans la déclaration de gestionnaire, au lieu d’attacher des gestionnaires avec des attributs dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Toutefois, cette technique a certaines limitations, car le `Handles` mot clé ne peut pas prendre en charge toutes les fonctionnalités spécifiques de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système des événements, tels que certains scénarios d’événements routés ou événements attachés. Pour plus d’informations, consultez [Visual Basic et la gestion des événements de WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x : Code  
 [x : Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) est un élément de directive défini dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Un `x:Code` la directive de l’élément peut contenir du code de programmation inline. Le code qui est définie en ligne peut interagir avec le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sur la même page. L’exemple suivant illustre inline [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] code. Notez que le code se trouve dans le `x:Code` élément et que le code doit être entouré de `<CDATA[`... `]]>` pour échapper le contenu pour [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], de sorte qu’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur (interprétant le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schéma ou la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schéma) n’essaiera pas d’interpréter le contenu littéralement en tant que [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Limitations de Code inline  
 Vous devez envisager les éviter ou limiter l’utilisation de code inline. En termes d’architecture et de philosophie du codage, la séparation entre le balisage et code-behind conserve les rôles de concepteurs et les développeurs beaucoup plus distinctes. Sur un niveau plus technique, le code que vous écrivez pour le code inline peut être plus difficile à écrire, étant donné que vous écrivez toujours dans la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] classe partielle générée et pouvez utiliser uniquement les mappages d’espace de noms XML par défaut. Étant donné que vous ne pouvez pas ajouter `using` instructions, vous devez qualifier entièrement la plupart de la [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] les appels que vous apportez. La valeur par défaut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mappages incluent la plupart mais pas tous les [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] espaces de noms qui sont présents dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] assemblys ; vous devez qualifier pleinement les appels aux types et membres contenus dans les autres espaces de noms CLR. Vous également ne peut pas définir au-delà de la classe partielle dans le code inline, et toutes les entités de code utilisateur que vous référencez doivent exister en tant que membre ou variable dans la classe partielle générée. Autres langue des fonctionnalités de programmation, tels que les macros ou `#ifdef` pour les variables globales ou les variables de génération, ne sont pas disponibles. Pour plus d’informations, consultez [x : Code de Type XAML intrinsèque](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [x:Code, type XAML intrinsèque](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [Génération d’une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
