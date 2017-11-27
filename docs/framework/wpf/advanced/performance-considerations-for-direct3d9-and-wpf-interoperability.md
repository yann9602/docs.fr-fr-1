---
title: "Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], Direct3D9 interop performance
- Direct3D9 [WPF interoperability], performance
ms.assetid: ea8baf91-12fe-4b44-ac4d-477110ab14dd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 886ef6c8c9df9d14b5c2a805da2e3948d5e55f69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="performance-considerations-for-direct3d9-and-wpf-interoperability"></a>Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF
Vous pouvez héberger le contenu Direct3D9 à l’aide de la <xref:System.Windows.Interop.D3DImage> classe. Hébergement du contenu de Direct3D9 peut affecter les performances de votre application. Cette rubrique décrit les meilleures pratiques pour optimiser les performances lors de l’hébergement de contenu Direct3D9 dans une application Windows Presentation Foundation (WPF). Ces meilleures pratiques incluent l’utilisation de <xref:System.Windows.Interop.D3DImage> et les meilleures pratiques lorsque vous utilisez Windows Vista, Windows XP, et affiche des écrans multiples.  
  
> [!NOTE]
>  Pour obtenir des exemples de code qui illustrent ces meilleures pratiques, consultez [WPF et Direct3D9 interopérabilité](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="use-d3dimage-sparingly"></a>Utilisez avec modération de D3DImage  
 Le contenu Direct3D9 hébergé dans un <xref:System.Windows.Interop.D3DImage> instance ne rend pas aussi rapide que dans une application Direct3D pure. Copie de la surface et de vider le tampon de commande peuvent être des opérations coûteuses. Comme le nombre de <xref:System.Windows.Interop.D3DImage> augmente d’instances, plus se produit et dégradent les performances. Par conséquent, vous devez utiliser <xref:System.Windows.Interop.D3DImage> avec parcimonie.  
  
## <a name="best-practices-on-windows-vista"></a>Meilleures pratiques sur Windows Vista  
 Pour de meilleures performances sur Windows Vista avec un affichage qui est configuré pour utiliser le modèle de pilote d’affichage de Windows (WDDM), créez votre surface Direct3D9 sur un `IDirect3DDevice9Ex` appareil. Cela permet le partage de surface. La carte vidéo doit prendre en charge la `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` et `D3DCAPS2_CANSHARERESOURCE` fonctionnalités du pilote sur Windows Vista. Tous les autres paramètres entraînent la surface à être copiée via le logiciel, ce qui réduit considérablement les performances.  
  
> [!NOTE]
>  Si Windows Vista a un affichage qui est configuré pour utiliser le modèle de pilote d’affichage de Windows XP (XDDM), la surface est toujours copiée via le logiciel, indépendamment des paramètres. Avec les paramètres appropriés et de la carte vidéo, vous verrez meilleures performances sur Windows Vista lorsque vous utilisez le WDDM, car la copie de la surface est effectuées dans le matériel.  
  
## <a name="best-practices-on-windows-xp"></a>Meilleures pratiques sur Windows XP  
 Pour de meilleures performances sur Windows XP, qui utilise le modèle de pilote affichage (XDDM) de Windows XP, créez une surface verrouillable qui se comporte correctement lorsque le `IDirect3DSurface9::GetDC` méthode est appelée. En interne, le `BitBlt` méthode transfère la surface pour les appareils dans le matériel. Le `GetDC` méthode fonctionne toujours sur les surfaces XRGB. Toutefois, si l’ordinateur client exécute Windows XP avec SP3 ou SP2, et si le client a également le correctif logiciel pour la fonctionnalité de superposition des fenêtres, cette méthode fonctionne uniquement sur les surfaces ARVB. La carte vidéo doit prendre en charge la `D3DDEVCAPS2_CAN_STRETCHRECT_FROM_TEXTURES` fonctionnalité de pilote.  
  
 Une profondeur de l’affichage du bureau 16 bits peut réduire considérablement les performances. Un ordinateur 32 bits est recommandé.  
  
 Si vous développez pour Windows Vista et Windows XP, testez les performances sur Windows XP. Exécution de la mémoire vidéo sur Windows XP est une préoccupation. En outre, <xref:System.Windows.Interop.D3DImage> sur Windows XP utilise plus de mémoire vidéo et de bande passante que Windows Vista WDDM, en raison d’une copie de mémoire vidéo supplémentaire nécessaire. Par conséquent, vous pouvez prévoir les performances soient moins bonnes sur Windows XP que sur Windows Vista pour le même matériel vidéo.  
  
> [!NOTE]
>  XDDM est disponible sur Windows XP et Windows Vista. Toutefois, WDDM est disponible uniquement sur Windows Vista.  
  
## <a name="general-best-practices"></a>Meilleures pratiques générales  
 Lorsque vous créez le périphérique, utilisez le `D3DCREATE_MULTITHREADED` indicateur de création. Cela réduit les performances, mais le système de rendu WPF appelle les méthodes sur ce périphérique à partir d’un autre thread. Veillez à suivre le protocole de verrouillage correctement, afin qu’aucun des deux threads y accéder en même temps.  
  
 Si votre rendu est exécuté sur un thread managé WPF, il est fortement recommandé de créer le périphérique avec le `D3DCREATE_FPU_PRESERVE` indicateur de création. Sans ce paramètre, le rendu D3D peut réduire la précision des opérations à double précision WPF et de présenter des problèmes de rendu.  
  
 Affichage en mosaïque un <xref:System.Windows.Interop.D3DImage> est rapide, sauf si vous disposer en mosaïque une surface non pow2 sans prise en charge matérielle, ou si vous mettez en mosaïque une <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush> qui contient un <xref:System.Windows.Interop.D3DImage>.  
  
## <a name="best-practices-for-multi-monitor-displays"></a>Meilleures pratiques pour l’affichage sur plusieurs écrans  
 Si vous utilisez un ordinateur qui dispose de plusieurs moniteurs, vous devez suivre les meilleures pratiques décrites précédemment. Il existe également certaines considérations supplémentaires sur les performances d’une configuration à plusieurs écran.  
  
 Lorsque vous créez la mémoire tampon d’arrière-plan, il est créé sur un périphérique spécifique et l’adaptateur, mais WPF peut afficher le tampon d’affichage sur toutes les cartes. Copie pour des adaptateurs pour mettre à jour le tampon d’affichage peut être très coûteuse. Sur Windows Vista, qui est configuré pour utiliser le WDDM avec plusieurs cartes vidéos et un `IDirect3DDevice9Ex` appareil, si le tampon d’affichage se trouve sur un autre adaptateur mais toujours sur la même carte vidéo, il n’existe aucune altération des performances. Toutefois, sur Windows XP et le XDDM possède plusieurs cartes vidéo, il est sensiblement les performances lorsque le tampon d’affichage s’affiche sur un autre adaptateur que la mémoire tampon d’arrière-plan. Pour plus d’informations, consultez [WPF et Direct3D9 interopérabilité](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md).  
  
## <a name="performance-summary"></a>Résumé des performances  
 Le tableau suivant montre les performances de la mise à jour du tampon d’affichage en fonction du système d’exploitation, le format de pixel et verrouillabilité de la surface. Le tampon d’affichage et de la mémoire tampon d’arrière-plan sont supposées pour se trouver sur la même carte. Selon la configuration de la carte, les mises à jour matérielles sont généralement beaucoup plus rapides que les mises à jour logicielles.  
  
|Format de pixel de la surface|9Ex, WDDM et Windows Vista|Autres configurations Windows Vista|Windows XP SP3 ou SP2 avec correctif logiciel|Windows XP SP2|  
|--------------------------|---------------------------------|----------------------------------------|--------------------------------------|--------------------|  
|D3DFMT_X8R8G8B8 (non verrouillable)|**Mise à jour du matériel**|Mise à jour logicielle|Mise à jour logicielle|Mise à jour logicielle|  
|D3DFMT_X8R8G8B8 (verrouillable)|**Mise à jour du matériel**|Mise à jour logicielle|**Mise à jour du matériel**|**Mise à jour du matériel**|  
|D3DFMT_A8R8G8B8 (non verrouillable)|**Mise à jour du matériel**|Mise à jour logicielle|Mise à jour logicielle|Mise à jour logicielle|  
|D3DFMT_A8R8G8B8 (verrouillable)|**Mise à jour du matériel**|Mise à jour logicielle|**Mise à jour du matériel**|Mise à jour logicielle|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Interop.D3DImage>  
 [Interopérabilité WPF et Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
 [Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
