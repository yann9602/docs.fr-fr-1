---
title: "Consid&#233;rations sur les performances de l&#39;interop&#233;rabilit&#233; entre Direct3D9 et WPF | Microsoft Docs"
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
  - "Direct3D9 (interopérabilité WPF), performances"
  - "WPF, performance d'interopérabilité Direct3D9"
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Consid&#233;rations sur les performances de l&#39;interop&#233;rabilit&#233; entre Direct3D9 et WPF
Vous pouvez héberger du contenu Direct3D9 à l'aide de la classe <xref:System.Windows.Interop.D3DImage>.  L'hébergement de contenu Direct3D9 risque d'altérer les performances de votre application.  Cette rubrique décrit les meilleures pratiques permettant d'optimiser les performances en cas d''hébergement de contenu Direct3D9 dans une application Windows Presentation Foundation \(WPF\) :  Meilleures pratiques relatives à l'utilisation de la classe <xref:System.Windows.Interop.D3DImage> et meilleures pratiques en cas d'utilisation de Windows Vista et de Windows XP et d'affichage sur plusieurs écrans.  
  
> [!NOTE]
>  Pour obtenir des exemples de code qui illustrent ces meilleures pratiques, consultez [Interopérabilité WPF et Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## Utilisation avec modération de D3DImage  
 Le contenu Direct3D9 hébergé dans une instance <xref:System.Windows.Interop.D3DImage> n'est pas aussi rapidement restitué que dans une application Direct3D à proprement parler.  La copie de la surface et le vidage du tampon de commande risquent de devenir des opérations coûteuses.  Plus le nombre d'instances <xref:System.Windows.Interop.D3DImage> est élevé, plus la quantité de vidages augmente et plus les performances se dégradent.  Vous devez par conséquent utiliser <xref:System.Windows.Interop.D3DImage> avec modération.  
  
## Meilleures pratiques sur Windows Vista  
 Pour optimiser les performances sur Windows Vista avec un affichage configuré pour utiliser le modèle de pilote d'affichage de Windows \(WDDM\), créez votre surface Direct3D9 sur un périphérique `IDirect3DDevice9Ex`.  Cela active le partage de surface.  La carte vidéo doit prendre en charge les fonctionnalités de pilote `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` et `D3DCAPS2_CANSHARERESOURCE` sur Windows Vista.  Tous les autres paramètres entraînent la copie de la surface via le logiciel, ce qui altère considérablement les performances.  
  
> [!NOTE]
>  Si l'affichage est configuré sur Windows Vista pour utiliser le modèle de pilote d'affichage de Windows XP \(XDDM\), la surface est systématiquement copiée via le logiciel, quels que soient les paramètres.  Lorsque vous utiliserez le WDDM avec la carte vidéo et les paramètres appropriés, vous constaterez de meilleures performances sur Windows Vista, car la copie de la surface s'effectue au niveau matériel.  
  
## Meilleures pratiques sur Windows XP  
 Pour optimiser les performances sur Windows XP en cas d'utilisation du modèle de pilote d'affichage de Windows XP \(XDDM\), créez une surface verrouillable qui se comporte correctement lorsque la méthode `IDirect3DSurface9::GetDC` est appelée.  En interne, la méthode `BitBlt` transfère la surface via les périphériques au niveau matériel.  La méthode `GetDC` fonctionne toujours sur les surfaces XRGB.  Toutefois, si l'ordinateur client exécute Windows XP SP3 ou SP2, et si le client dispose également du correctif logiciel pour la fonctionnalité de superposition des fenêtres, cette méthode fonctionne uniquement sur les surfaces ARGB.  La carte vidéo doit prendre en charge la fonctionnalité de pilote `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES`.  
  
 Une profondeur d'affichage de bureau de 16 bits risque d'altérer considérablement les performances.  Un bureau de 32 bits est recommandé.  
  
 Si vous développez pour Windows Vista et Windows XP, testez les performances sur Windows XP.  La saturation de la mémoire vidéo pose problème sur Windows XP.  De plus, <xref:System.Windows.Interop.D3DImage> utilise plus de mémoire vidéo et de bande passante sur Windows XP que sur le WDDM de Windows Vista, car des copies supplémentaires s'avèrent nécessaires dans la mémoire vidéo.  Par conséquent, vous pouvez vous attendre à ce que les performances soient moins bonnes sur Windows XP que sur Windows Vista pour le même matériel vidéo.  
  
> [!NOTE]
>  Le XDDM est disponible à la fois sur Windows XP et sur Windows Vista, mais le WDDM n'est disponible que sur Windows Vista.  
  
## Meilleures pratiques en général  
 Lorsque vous créez le périphérique, utilisez l'indicateur de création `D3DCREATE_MULTITHREADED`.  Cela altère les performances, mais le système de rendu WPF appelle les méthodes à partir d'un autre thread sur ce périphérique.  Veillez à appliquer correctement le protocole de verrouillage, de sorte qu'aucun des deux threads ne puisse accéder simultanément au périphérique.  
  
 Si votre rendu est exécuté sur un thread managé WPF, il est vivement recommandé de créer le périphérique avec l'indicateur de création `D3DCREATE_FPU_PRESERVE`.  Sans ce paramètre, le rendu D3D risque de rendre des opérations en double précision WPF imprécises et de créer des problèmes de rendu.  
  
 La disposition en mosaïque d'un <xref:System.Windows.Interop.D3DImage> est rapide, sauf si vous disposez en mosaïque une surface non pow2 sans prise en charge matérielle ou si vous disposez en mosaïque un <xref:System.Windows.Media.DrawingBrush> ou un <xref:System.Windows.Media.VisualBrush> qui contient un <xref:System.Windows.Interop.D3DImage>.  
  
## Meilleures pratiques relatives à l'affichage sur plusieurs écrans  
 Si vous utilisez un ordinateur qui possède plusieurs écrans, vous devez suivre les meilleures pratiques préalablement décrites.  Vous devez également tenir compte d'autres considérations sur les performances lors de la configuration de plusieurs écrans.  
  
 Lorsque vous créez la mémoire tampon d'arrière\-plan, celle\-ci est créée sur un périphérique et un adaptateur spécifiques, mais WPF peut afficher le tampon d'affichage sur n'importe quel adaptateur.  La copie d'un adaptateur à un autre pour mettre à jour le tampon d'affichage peut s'avérer très coûteuse.  Si Windows Vista est configuré pour utiliser le WDDM avec plusieurs cartes vidéo et un périphérique `IDirect3DDevice9Ex` et que le tampon d'affichage se trouve sur un autre adaptateur mais toujours sur la même carte vidéo, les performances ne s'en trouvent pas altérées.  Si le XDDM possède plusieurs cartes vidéo sur Windows XP et que le tampon d'affichage s'affiche sur un autre adaptateur que la mémoire tampon d'arrière\-plan, les performances s'en trouvent considérablement altérées.  Pour plus d'informations, consultez [Interopérabilité WPF et Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## Résumé des performances  
 Le tableau suivant indique les performances de mise à jour du tampon d'affichage sur plusieurs plans : fonction du système d'exploitation, format de pixel et verrouillabilité de la surface.  Nous partons du principe que le tampon d'affichage et la mémoire tampon d'arrière\-plan se trouvent sur le même adaptateur.  Selon la configuration de l'adaptateur, les mises à jour matérielles sont généralement beaucoup plus rapides que les mises à jour logicielles.  
  
|Format de pixel de la surface|Windows Vista, WDDM et 9Ex|Autres configurations Windows Vista|Windows XP SP3 ou SP2 avec correctif logiciel|Windows XP SP2|  
|-----------------------------------|--------------------------------|-----------------------------------------|---------------------------------------------------|--------------------|  
|D3DFMT\_X8R8G8B8 \(non verrouillable\)|**Mise à jour matérielle**|Mise à jour logicielle|Mise à jour logicielle|Mise à jour logicielle|  
|D3DFMT\_X8R8G8B8 \(verrouillable\)|**Mise à jour matérielle**|Mise à jour logicielle|**Mise à jour matérielle**|**Mise à jour matérielle**|  
|D3DFMT\_A8R8G8B8 \(non verrouillable\)|**Mise à jour matérielle**|Mise à jour logicielle|Mise à jour logicielle|Mise à jour logicielle|  
|D3DFMT\_A8R8G8B8 \(verrouillable\)|**Mise à jour matérielle**|Mise à jour logicielle|**Mise à jour matérielle**|Mise à jour logicielle|  
  
## Voir aussi  
 <xref:System.Windows.Interop.D3DImage>   
 [Interopérabilité WPF et Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)   
 [Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)   
 [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)