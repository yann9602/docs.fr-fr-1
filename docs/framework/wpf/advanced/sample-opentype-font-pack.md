---
title: Exemple de pack de polices OpenType
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbc5caeab5a77518e160bacb9722e50ff7abbfb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sample-opentype-font-pack"></a>Exemple de pack de polices OpenType
Cette rubrique fournit une vue d’ensemble des polices d’exemple [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] qui sont distribuées avec le [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]. Les exemples de polices prennent en charge des fonctionnalités [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] étendues qui peuvent être utilisées par les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Polices du pack de polices OpenType  
 Le [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] contient des exemples de polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] que vous pouvez utiliser lorsque vous créez des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Les exemples de polices sont fournis sous licence Ascender Corporation. Ces polices implémentent uniquement une partie des fonctionnalités définies par le format [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]. Le tableau suivant répertorie les exemples de polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)].  
  
|**Nom**|**Fichier**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 L’illustration suivante montre à quoi ressemblent les exemples de polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)].  
  
 ![Liste des noms de police dans l’exemple de pack de police](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")  
Polices du pack de polices OpenType  
  
 Les exemples de polices sont fournis sous licence Ascender Corporation. Ascender est un fournisseur de polices avancées. Pour obtenir une licence des versions étendues ou personnalisées des exemples de polices, consultez le [site web d’Ascender Corporation](http://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
>  En tant que développeur, vous devez vérifier que vous disposez des droits de licence nécessaires pour toute police incorporée dans une application ou redistribuée.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Installation des polices  
 Vous pouvez installer les exemples de polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dans le répertoire de polices [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] par défaut **\WINDOWS\Fonts**. Utilisez le panneau de configuration des polices pour installer les polices. Une fois que les polices sont installées sur votre ordinateur, elles sont accessibles à toutes les applications qui référencent les polices [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] par défaut. Pour afficher un jeu de caractères représentatif dans plusieurs tailles de police, double-cliquez sur le fichier de police. La capture d’écran suivante montre le fichier de police Lindsey, Linds.ttf.  
  
 ![Police Lindsey &#40; OpenType &#41; ] (../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")  
Affichage de la police Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Utilisation des polices  
 Vous pouvez utiliser des polices dans votre application de deux manières. Vous pouvez ajouter des polices à votre application sous forme d’éléments de contenu de projet qui ne sont pas incorporés comme des ressources d’assembly. Vous pouvez également ajouter des polices à votre application sous forme d’éléments de ressource de projet incorporés qui sont incorporés dans les fichiers d’assembly de l’application. Pour plus d’informations, consultez [Empaquetage de polices avec des applications](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Documents.Typography>  
 [Fonctionnalités des polices OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Empaquetage de polices avec des applications](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
