---
title: "Param&#232;tres du Registre pour le rendu des graphiques | Microsoft Docs"
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
  - "graphiques (WPF), rendu"
  - "restituer des graphiques"
  - "restituer des graphiques, paramètres du Registre"
  - "restituer des graphiques, dépanner"
  - "dépanner le rendu de graphiques"
ms.assetid: f4b41b42-327d-407c-b398-3ed5f505df8b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Param&#232;tres du Registre pour le rendu des graphiques
Cette rubrique donne une vue d'ensemble des paramètres du Registre pour le rendu des graphiques [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui affectent les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="overview"></a>   
## Quand utiliser les paramètres du Registre pour le rendu des graphiques  
 Ces paramètres du Registre sont destinés à dépanner, déboguer les applications et fournir un support technique pour les produits.  Étant donné que les modifications apportées au Registre affectent toutes les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], votre application ne doit jamais modifier ces clés de Registre de façon automatique ni pendant l'installation.  
  
<a name="xpdmandwddm"></a>   
## Que sont XPDM et WDDM ?  
 Certains paramètres du Registre pour le rendu des graphiques ont des valeurs par défaut différentes, selon le pilote utilisé par votre carte vidéo : XPDM ou WDDM.  XPDM est le modèle de pilote d'affichage de [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] et WDDM est le modèle de pilote d'affichage de Windows.  WDDM est disponible sur les ordinateurs qui exécutent [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] et [!INCLUDE[win7](../../../../includes/win7-md.md)].  XPDM est disponible sur les ordinateurs qui exécutent [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)], [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] et [!INCLUDE[TLA#tla_winnetsvrfam](../../../../includes/tlasharptla-winnetsvrfam-md.md)].  Pour plus d'informations sur WDDM, consultez [Windows Vista Display Driver Model](http://go.microsoft.com/fwlink/?LinkId=178394).  
  
<a name="registry_settings"></a>   
## Paramètres du Registre  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit quatre paramètres du Registre pour contrôler le rendu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
|Paramètre|Description|  
|---------------|-----------------|  
|**Désactiver l'option d'accélération matérielle**|Spécifie si l'accélération matérielle doit être activée.|  
|**Valeur d'échantillonnage multiple maximale**|Spécifie le degré d'échantillonnage multiple pour l'anticrénelage de contenu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].|  
|**Paramètre de la date du pilote vidéo requis**|Spécifie si le système désactive l'accélération matérielle pour les pilotes commercialisés avant novembre 2004.|  
|**Utiliser l'option du module de rastérisation de référence**|Spécifie si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] doit utiliser le module de rastérisation de référence.|  
  
 Ces paramètres sont accessibles à tout utilitaire de configuration externe capable de référencer les paramètres du Registre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Ils peuvent également être créés ou modifiés en accédant directement aux valeurs en utilisant l'Éditeur du Registre [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
<a name="disablehardwareacceleration"></a>   
## Désactiver l'option d'accélération matérielle  
  
|Clé de Registre|Type valeur|  
|---------------------|-----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\DisableHWAcceleration`|DWORD|  
  
 L'option **Désactiver l'option d'accélération matérielle** vous permet de désactiver l'accélération matérielle pour effectuer un débogage et des tests.  Si vous voyez des artefacts de rendu dans une application, essayez de désactiver l'accélération matérielle.  Si les artefacts disparaissent, le problème est peut\-être lié à votre pilote vidéo.  
  
 **Désactiver l'option d'accélération matérielle** est une valeur DWORD qui est 0 ou 1.  La valeur 1 désactive l'accélération matérielle.  La valeur 0 active l'accélération matérielle, à condition que le système soit conforme aux exigences relatives à l'accélération ; pour plus d'informations, consultez [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
<a name="maxmultisample"></a>   
## Valeur d'échantillonnage multiple maximale  
  
|Clé de Registre|Type valeur|  
|---------------------|-----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\MaxMultisampleType`|DWORD|  
  
 L'option **Valeur d'échantillonnage multiple maximale** vous permet d'ajuster la quantité maximale de l'anticrénelage du contenu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  Utilisez\-la pour désactiver l'anticrénelage [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] ou pour l'activer dans [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].  
  
 La **valeur d'échantillonnage multiple maximale** est une valeur DWORD qui varie entre 0 et 16.  La valeur 0 spécifie que l'anticrénelage d'échantillonnage multiple du contenu 3D doit être désactivé, et la valeur 16 essaiera d'utiliser jusqu'à 16 anticrénelages d'échantillonnages multiples, en cas de prise en charge par la carte vidéo.  Attention, la définition de cette valeur de clé de Registre sur les ordinateurs à l'aide de pilotes XPDM entraînera la conséquence suivante : les applications utiliseront une grande quantité de mémoire vidéo supplémentaire, réduisant ainsi la performance du rendu [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]. Elle pourra également introduire des erreurs de rendu et des problèmes de stabilité.  
  
 Si cette clé n'est pas configurée, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise par défaut la valeur 0 pour les pilotes XPDM et la valeur 4 pour les pilotes WDDM.  
  
<a name="requiredvideodriverdatesetting"></a>   
## Paramètre de la date du pilote vidéo requis  
  
|Clé de Registre|Type valeur|  
|---------------------|-----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\RequiredVideoDriverDate`|Chaîne|  
  
 En novembre 2004, [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] a publié une nouvelle version des indications relatives aux tests des pilotes ; les pilotes créés après cette date offre une meilleure stabilité.  Par défaut, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le pipeline d'accélération matérielle pour ces pilotes et revient au rendu logiciel pour les pilotes XPDM publiés avant cette date.  
  
 L'option **Paramètre de la date du pilote vidéo requis** vous permet de spécifier une autre date minimale pour les pilotes XPDM.  Vous devez indiquer une date antérieure à novembre 2004 uniquement si vous êtes sûr que votre pilote vidéo est assez stable pour prendre en charge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 La chaîne de ce paramètre a le format suivant :  
  
||  
|-|  
|*AAAA* `/` *MM* `/` *JJ*|  
  
 où *AAAA* correspond aux quatre chiffres de l'année, *MM* aux deux chiffres du mois et *JJ* aux deux chiffres du jour.  Si cette valeur n'est pas définie, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise novembre 2004 comme date du pilote vidéo requis.  
  
<a name="usereferencerasterizeroption"></a>   
## Utiliser l'option du module de rastérisation de référence  
  
|Clé de Registre|Type valeur|  
|---------------------|-----------------|  
|`HKEY_CURRENT_USER\SOFTWARE\Microsoft\Avalon.Graphics\UseReferenceRasterizer`|DWORD|  
  
 L'option **Utiliser l'option du module de rastérisation de référence** vous permet de forcer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à passer en mode de rendu matériel simulé pour le débogage : [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] passe en mode matériel, mais utilise le rastériseur logiciel de référence [!INCLUDE[TLA#tla_d3d](../../../../includes/tlasharptla-d3d-md.md)], d3dref9.dll, au lieu d'un périphérique matériel réel.  
  
 Le rastériseur de référence est très lent, mais ignore votre pilote vidéo pour éviter tout problème de rendu provoqué par des problèmes dus aux pilotes.  C'est pourquoi vous pouvez utiliser le rastériseur de référence pour déterminer si les problèmes de rendu sont liés au pilote vidéo.  Le fichier d3dref9.dll doit être dans un emplacement accessible par l'application, par exemple dans le chemin d'accès du système ou le répertoire local de l'application.  
  
 L'option **Utiliser l'option du module de rastérisation de référence** prend une valeur DWORD.  La valeur 0 indique le rastériseur de référence n'est pas utilisé.  Toute autre valeur force [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à utiliser le rastériseur de référence.  
  
## Voir aussi  
 [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)