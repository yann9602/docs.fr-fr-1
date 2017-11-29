---
title: Guide pratique pour utiliser SystemParameters
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
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4b2ee3956017e10da8adda52fa9a0ec31cb19ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemparameters"></a>Guide pratique pour utiliser SystemParameters
Cet exemple montre comment accéder à et utiliser les propriétés de <xref:System.Windows.SystemParameters> afin d’appliquer un style ou personnaliser un bouton.  
  
## <a name="example"></a>Exemple  
 Les ressources système exposent plusieurs paramètres système en tant que ressources pour vous aider à créer des visuels cohérents avec les paramètres système. <xref:System.Windows.SystemParameters>est une classe qui contient à la fois des propriétés de valeur de paramètre système et des clés de ressources liées aux valeurs. Par exemple, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> est un <xref:System.Windows.SystemParameters> valeur de propriété et <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> est la clé de ressource correspondante.  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez utiliser les membres de <xref:System.Windows.SystemParameters> comme utilisation de propriété statique ou un fait référence à une ressource dynamique (avec la valeur de propriété statique en tant que la clé). Utilisez une référence de ressource dynamique si vous souhaitez que la valeur système soit mise à jour automatiquement pendant que l’application s’exécute ; sinon, utilisez une référence statique. Les clés de ressources ont le suffixe `Key` ajouté au nom de propriété.  
  
 L’exemple suivant montre comment accéder à et utiliser des valeurs statiques de <xref:System.Windows.SystemParameters> pour appliquer un style ou personnaliser un bouton. Cet exemple de balisage dimensionne un bouton en appliquant <xref:System.Windows.SystemParameters> valeurs à un bouton.  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 Pour utiliser les valeurs de <xref:System.Windows.SystemParameters> dans le code, vous n’avez pas à utiliser des références statiques ou références de ressources dynamiques. Au lieu de cela, utilisez les valeurs de la <xref:System.Windows.SystemParameters> classe. Bien que les propriétés non clé soient apparemment définies en tant que propriétés statiques, le comportement d’exécution de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comme hébergé par le système sera réévalue les propriétés en temps réel, et tient compte des modifications utilisateur apportées aux valeurs système. L’exemple suivant montre comment définir la largeur et la hauteur d’un bouton à l’aide de <xref:System.Windows.SystemParameters> valeurs.  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.SystemParameters>  
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Utiliser des SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Utiliser les clés des paramètres système](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
