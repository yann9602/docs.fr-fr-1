---
title: "Paramètres du Registre ClearType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ClearType [WPF], registry settings
- typography [WPF], ClearType registry settings
ms.assetid: 56f314bb-b30b-4f67-8492-8b8a9fa432ae
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc4411c8141579150cde1bda2e46d7d2abe42e9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cleartype-registry-settings"></a>Paramètres du Registre ClearType
Cette rubrique fournit une vue d’ensemble de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] les paramètres du Registre qui sont utilisées par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.  
  
  
<a name="overview"></a>   
## <a name="technology-overview"></a>Vue d’ensemble de la technologie  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications qui restituent le texte à un périphérique d’affichage utilisent [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] fonctionnalités pour fournir une expérience de lecture améliorée. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] est une technologie logicielle développée par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] qui améliore la lisibilité du texte sur les écrans LCD existants, tels que les écrans d’ordinateurs portables, les écrans de Pocket PC et les écrans plats. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] fonctionne en accédant aux éléments individuels de la bande de couleur verticale dans chaque pixel d’un écran LCD. Pour plus d’informations sur [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], consultez [vue d’ensemble de ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 Texte restitué avec [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] peut apparaître considérablement différent lorsqu’ils sont affichés sur différents périphériques d’affichage. Par exemple, un petit nombre de moniteurs implémentent les éléments de bande de couleur dans l’ordre bleu, vert, rouge au lieu du plus courant rouge, vert, bleu ( [!INCLUDE[TLA#tla_rgb](../../../../includes/tlasharptla-rgb-md.md)]) ordre.  
  
 Texte restitué avec [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] peut également apparaître considérablement différent lorsqu’ils sont affichés par des personnes ayant des niveaux de sensibilité de couleur. Certains individus peuvent détecter mieux que d’autres les variations chromatiques légères.  
  
 Dans chacun de ces cas, [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] fonctionnalités doivent être modifiés afin de fournir la meilleure expérience de lecture pour chaque personne.  
  
<a name="registry_settings"></a>   
## <a name="registry-settings"></a>Paramètres du Registre  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Spécifie les quatre paramètres du Registre pour contrôler [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] fonctionnalités :  
  
|Paramètre|Description|  
|-------------|-----------------|  
|Niveau [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]|Décrit le niveau de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] de couleur plus de clarté.|  
|Niveau gamma|Décrit le niveau du composant de couleur des pixels d’un écran d’affichage.|  
|Structure des pixels|Décrit la disposition des pixels d’un écran d’affichage.|  
|Niveau de contraste du texte|Décrit le niveau de contraste du texte affiché.|  
  
 Ces paramètres sont accessibles par un utilitaire de configuration externe qui sait comment référencer le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] paramètres du Registre. Ces paramètres peuvent également être créés ou modifiés en accédant directement aux valeurs à l’aide de l’Éditeur du Registre [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 Si le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] paramètres du Registre ne sont pas définies (c'est-à-dire l’état par défaut), le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] requêtes d’application le [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] informations relatives aux paramètres système pour les paramètres de lissage des polices.  
  
> [!NOTE]
>  Pour plus d’informations sur l’énumération des noms de périphérique d’affichage, consultez la `SystemParametersInfo` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (fonction).  
  
<a name="ClearType_level"></a>   
## <a name="cleartype-level"></a>Niveau ClearType  
 Le [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] niveau vous permet d’ajuster le rendu de texte basé sur le respect de la couleur et la perception d’un individu. Pour certaines personnes, le rendu de texte qui utilise [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] à son niveau le plus élevé ne produit pas la meilleure expérience de lecture.  
  
 Le [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] niveau est une valeur entière comprise entre 0 et 100. Le niveau par défaut est 100, ce qui signifie [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] utilise la capacité maximale des éléments de bande de couleur du périphérique d’affichage. Toutefois, un [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] niveau 0 restitue le texte en nuances de gris. En définissant le [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] niveau comprise entre 0 et 100, vous pouvez créer un niveau intermédiaire qui convient pour le respect de la couleur d’un individu.  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 L’emplacement du paramètre de Registre pour le [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] niveau est un paramètre utilisateur individuel qui correspond à un nom de périphérique d’affichage spécifique :  
  
 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage pour un utilisateur, un `ClearTypeLevel` valeur DWORD est définie. La capture d’écran suivante affiche le paramètre de l’Éditeur du Registre pour le [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] niveau.  
  
 ![Paramètres ClearType dans l’Éditeur de Registre](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]applications afficher le texte dans un des deux modes, avec ou sans [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]. Lorsque le texte est restitué sans [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], il est appelé rendu de nuances de gris.  
  
<a name="gamma_level"></a>   
## <a name="gamma-level"></a>Niveau gamma  
 Le niveau gamma fait référence à la relation non linéaire entre une valeur de pixel et la luminance. Ce paramètre doit correspondre aux caractéristiques physiques de l’écran d’affichage ; dans le cas contraire, des distorsions dans le rendu pourraient se produire. Par exemple, un test peut apparaître trop large ou trop étroit, ou encore des franges de couleurs peuvent apparaître sur les bords des traits verticaux des glyphes.  
  
 Le niveau gamma est une valeur entière comprise entre 1 000 et 2 200. Le niveau par défaut est 1 900.  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 Le paramètre du Registre du niveau gamma se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage pour un utilisateur, un `GammaLevel` valeur DWORD est définie. La capture d’écran suivante indique le paramètre du niveau gamma dans l’Éditeur du Registre.  
  
 ![Paramètres ClearType dans l’Éditeur de Registre](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="pixel_structure"></a>   
## <a name="pixel-structure"></a>Structure des pixels  
 La structure des pixels décrit le type des pixels qui composent un écran d’affichage. Cette structure peut être de trois types :  
  
|Type|Valeur|Description|  
|----------|-----------|-----------------|  
|À deux dimensions|0|L’écran d’affichage n’a aucune structure de pixels. Cela signifie que les sources de lumière de chaque couleur sont étalées de manière uniforme sur la zone de pixel – ce rendu est appelé « rendu en échelle de gris ». C’est ainsi que fonctionne un écran d’affichage standard. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] n’est jamais appliqué au texte rendu.|  
|RVB|1|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : rouge, vert et bleu. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] est appliqué au texte rendu.|  
|BVR|2|L’écran d’affichage comporte des pixels constitués de trois bandes dans l’ordre suivant : bleu, vert et rouge. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] est appliqué au texte rendu. Notez que l’ordre est inversé par rapport au type RVB.|  
  
 La structure du pixel correspond à une valeur entière comprise entre 0 et 2. Le niveau par défaut est 0, qui représente une structure de pixel plate.  
  
> [!NOTE]
>  Pour plus d’informations sur l’énumération des noms de périphérique d’affichage, consultez la `EnumDisplayDevices` [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (fonction).  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 Le paramètre du Registre de la structure des pixels se trouve dans un paramètre d’ordinateur local correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage pour un utilisateur, un `PixelStructure` valeur DWORD est définie. La capture d’écran suivante indique le paramètre de la structure des pixels dans l’Éditeur du Registre.  
  
 ![Paramètres ClearType dans l’Éditeur de Registre](../../../../docs/framework/wpf/advanced/media/cleartyperegistry02.png "ClearTypeRegistry02")  
  
<a name="text_contrast_level"></a>   
## <a name="text-contrast-level"></a>Niveau de contraste du texte  
 Le niveau de contraste du texte vous permet d’ajuster le rendu du texte en fonction de la largeur de trait des glyphes. Le niveau de contraste du texte est une valeur entière comprise entre 0 et 6 ; plus cette valeur est élevée, plus le trait est épais. Le niveau par défaut est 1.  
  
### <a name="registry-setting"></a>Paramètre du Registre  
 Le paramètre du Registre du niveau de contraste du texte se trouve dans un paramètre utilisateur individuel correspondant à un nom d’écran d’affichage spécifique :  
  
 `HKEY_CURRENT_USER\Software\Microsoft\Avalon.Graphics\<displayName>`  
  
 Pour chaque nom de périphérique d’affichage pour un utilisateur, un `TextContrastLevel` valeur DWORD est définie. La capture d’écran suivante indique le paramètre du niveau de contraste du texte dans l’Éditeur du Registre.  
  
 ![Paramètres ClearType dans l’Éditeur de Registre](../../../../docs/framework/wpf/advanced/media/cleartyperegistry01.png "ClearTypeRegistry01")  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [Anticrénelage ClearType](https://msdn.microsoft.com/library/dd183433(v=vs.85).aspx)
