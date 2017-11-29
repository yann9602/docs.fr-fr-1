---
title: "Interopérabilité WPF et Direct3D9"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1bd4d7486f546a340a4c722d140c6c7f5cee707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-and-direct3d9-interoperation"></a>Interopérabilité WPF et Direct3D9
Vous pouvez inclure le contenu Direct3D9 dans une application Windows Presentation Foundation (WPF). Cette rubrique décrit comment créer le contenu Direct3D9 afin qu’elle interagit efficacement avec WPF.  
  
> [!NOTE]
>  Lorsque vous utilisez le contenu Direct3D9 dans WPF, vous devez également réfléchir aux performances. Pour plus d’informations sur la façon d’optimiser les performances, consultez [considérations sur les performances de Direct3D9 et interopérabilité WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
## <a name="display-buffers"></a>Mémoires tampons d’affichage  
 Le <xref:System.Windows.Interop.D3DImage> classe gère deux mémoires tampons d’affichage, qui sont appelés les *mémoire tampon d’arrière-plan* et *tampon d’affichage*. La mémoire tampon d’arrière-plan est votre surface Direct3D9. Modifications apportées à la mémoire tampon d’arrière-plan sont copiées en avant dans le tampon d’affichage lorsque vous appelez le <xref:System.Windows.Interop.D3DImage.Unlock%2A> (méthode).  
  
 L’illustration suivante montre la relation entre la mémoire tampon d’arrière-plan et le tampon d’affichage.  
  
 ![Mémoires tampons d’affichage D3DImage](../../../../docs/framework/wpf/advanced/media/d3dimage-buffers.png "D3DImage_buffers")  
  
## <a name="direct3d9-device-creation"></a>Création d’un périphérique Direct3D9  
 Pour restituer le contenu Direct3D9, vous devez créer un périphérique Direct3D9. Il existe deux objets Direct3D9 que vous pouvez utiliser pour créer un appareil, `IDirect3D9` et `IDirect3D9Ex`. Permet de créer ces objets `IDirect3DDevice9` et `IDirect3DDevice9Ex` périphériques, respectivement.  
  
 Créer un périphérique en appelant une des méthodes suivantes.  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Sur Windows Vista ou version ultérieure, utilisez le `Direct3DCreate9Ex` méthode avec un affichage qui est configuré pour utiliser le modèle de pilote d’affichage de Windows (WDDM). Utilisez la `Direct3DCreate9` méthode sur n’importe quelle autre plateforme.  
  
### <a name="availability-of-the-direct3dcreate9ex-method"></a>Disponibilité de la méthode Direct3DCreate9Ex  
 Le fichier d3d9.dll a la `Direct3DCreate9Ex` méthode uniquement sur Windows Vista ou version ultérieure. Si vous liez directement la fonction sur Windows XP, le chargement de votre application échoue. Pour déterminer si le `Direct3DCreate9Ex` méthode est prise en charge, de charger la DLL et recherchez l’adresse de procédure. Le code suivant montre comment tester le `Direct3DCreate9Ex` (méthode). Pour obtenir un exemple de code complet, consultez [procédure pas à pas : création de contenu Direct3D9 pour l’hébergement dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### <a name="hwnd-creation"></a>Création de HWND  
 Création d’un appareil nécessite un HWND. En règle générale, vous créez un HWND factice pour le Direct3D9 à utiliser. L’exemple de code suivant montre comment créer un HWND factice.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### <a name="present-parameters"></a>Paramètres présents  
 Création d’un périphérique requiert également une `D3DPRESENT_PARAMETERS` struct, mais seuls quelques paramètres sont importants. Ces paramètres sont choisis pour réduire l’encombrement mémoire.  
  
 Définir le `BackBufferHeight` et `BackBufferWidth` champs à 1. Les définissant sur 0 provoque leur être définie sur les dimensions du HWND.  
  
 Toujours défini le `D3DCREATE_MULTITHREADED` et `D3DCREATE_FPU_PRESERVE` pour éviter endommager la mémoire utilisée par Direct3D9 et empêcher Direct3D9 de modifier les paramètres FPU.  
  
 Le code suivant montre comment initialiser le `D3DPRESENT_PARAMETERS` struct.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## <a name="creating-the-back-buffer-render-target"></a>Création de la cible de rendu de mémoire tampon d’arrière-plan  
 Pour afficher le contenu Direct3D9 dans un <xref:System.Windows.Interop.D3DImage>, vous créez une surface Direct3D9 et l’assigner en appelant le <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> (méthode).  
  
### <a name="verifying-adapter-support"></a>Vérification de la prise en charge de l’adaptateur  
 Avant de créer une surface, vérifiez que toutes les cartes prennent en charge les propriétés de surface que vous avez besoin. Même si vous effectuez le rendu qu’une seule carte, la fenêtre WPF peut s’afficher sur n’importe quelle carte dans le système. Vous devez toujours écrire du code Direct3D9 qui gère les configurations de carte multi, et vous devez vérifier tous les adaptateurs pour la prise en charge, car WPF peut déplacer la surface parmi les adaptateurs disponibles.  
  
 L’exemple de code suivant montre comment vérifier toutes les cartes sur le système pour Direct3D9 prennent en charge.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### <a name="creating-the-surface"></a>Création de la Surface  
 Avant de créer une surface, vérifiez que les fonctionnalités prennent en charge les bonnes performances sur le système d’exploitation cible. Pour plus d’informations, consultez [considérations sur les performances de Direct3D9 et interopérabilité WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md).  
  
 Lorsque vous avez vérifié les fonctionnalités de l’appareil, vous pouvez créer la surface. L’exemple de code suivant illustre la création de la cible de rendu.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### <a name="wddm"></a>WDDM  
 Sur Windows Vista et les systèmes d’exploitation ultérieurs, qui sont configurés pour utiliser le WDDM, vous pouvez créer une texture de cible de rendu et passer la surface de niveau 0 pour le <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> (méthode). Cette approche n’est pas recommandée sur Windows XP, car vous ne pouvez pas créer une texture de cible de rendu verrouillable et les performances seront réduites.  
  
## <a name="handling-device-state"></a>Gestion d’état de l’appareil  
 Le <xref:System.Windows.Interop.D3DImage> classe gère deux mémoires tampons d’affichage, qui sont appelés les *mémoire tampon d’arrière-plan* et *tampon d’affichage*. La mémoire tampon d’arrière-plan est votre surface Direct3D.  Modifications apportées à la mémoire tampon d’arrière-plan sont copiées en avant dans le tampon d’affichage lorsque vous appelez le <xref:System.Windows.Interop.D3DImage.Unlock%2A> méthode, où il est affiché sur le matériel. Parfois, le tampon d’affichage n’est plus disponible. Ce manque de disponibilité peut résulter de verrouillage de l’écran, les applications Direct3D exclusives plein écran, changement d’utilisateur ou autres activités du système. Lorsque cela se produit, votre application WPF est notifiée en gérant le <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> événement.  Comment votre application répond à la mémoire tampon avant de devenir indisponibles dépend de l’activation à revenir au rendu logiciel WPF. Le <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> méthode a une surcharge qui accepte un paramètre qui spécifie si les WPF revient au rendu logiciel.  
  
 Lorsque vous appelez le <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> surcharge ou appelez le <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> surcharger avec la `enableSoftwareFallback` paramètre la valeur `false`, le système de rendu libère sa référence à la mémoire tampon d’arrière-plan lorsque le tampon d’affichage n’est plus disponible et que rien n’est affiché. Lorsque le tampon d’affichage est à nouveau disponible, le système de rendu déclenche le <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> événement pour avertir votre application WPF.  Vous pouvez créer un gestionnaire d’événements pour le <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> événement pour redémarrer le rendu avec une surface Direct3D valide. Pour redémarrer le rendu, vous devez appeler <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>.  
  
 Lorsque vous appelez le <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> surcharger avec la `enableSoftwareFallback` paramètre la valeur `true`, le système de rendu conserve sa référence à la mémoire tampon d’arrière-plan lorsque le tampon d’affichage n’est plus disponible, il est donc inutile d’appeler <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> lors de l’avant mémoire tampon est à nouveau disponible.  
  
 Lorsque le rendu logiciel est activé, il peut arriver dans lequel le périphérique l’utilisateur n’est plus disponible, mais le système de rendu conserve une référence à la surface Direct3D. Pour vérifier si un périphérique Direct3D9 n’est pas disponible, appelez le `TestCooperativeLevel` (méthode). Pour vérifier un appel de périphériques Direct3D9Ex le `CheckDeviceState` (méthode), car le `TestCooperativeLevel` méthode est déconseillée et retourne toujours une valeur. Si l’appareil de l’utilisateur n’est plus disponible, appelez <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> pour libérer la référence de WPF à la mémoire tampon d’arrière-plan.  Si vous devez réinitialiser votre appareil, appelez <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> avec la `backBuffer` paramètre la valeur `null`, puis appelez <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> avec `backBuffer` défini sur une surface Direct3D valide.  
  
 Appelez le `Reset` méthode pour récupérer à partir d’un périphérique non valide uniquement si vous implémentez la prise en charge comportant plusieurs carte. Sinon, libérer toutes les interfaces Direct3D9 et recréez-les complètement. Si la disposition des adaptateurs a changé, les objets Direct3D9 créés avant la modification ne sont pas mis à jour.  
  
## <a name="handling-resizing"></a>Gestion du redimensionnement  
 Si un <xref:System.Windows.Interop.D3DImage> s’affiche avec une résolution autre que sa taille d’origine, il est mis à l’échelle en fonction d’actuel <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>, sauf que <xref:System.Windows.Media.Effects.SamplingMode.Bilinear> est remplacé par <xref:System.Windows.Media.BitmapScalingMode.Fant>.  
  
 Si vous avez besoin d’une fidélité, vous devez créer un nouveau surface lorsque le conteneur de la <xref:System.Windows.Interop.D3DImage> change de taille.  
  
 Il existe trois approches possibles pour gérer le redimensionnement.  
  
-   Inclus dans le système de disposition et créer une surface lorsque la taille change. Ne créez pas trop de surfaces, car vous risquez de saturer ou de fragmenter la mémoire vidéo.  
  
-   Patientez jusqu'à ce qu’un événement de redimensionnement n’a pas eu lieu pour une période de temps pour créer la nouvelle surface.  
  
-   Créer un <xref:System.Windows.Threading.DispatcherTimer> qui vérifie les dimensions de conteneur plusieurs fois par seconde.  
  
## <a name="multi-monitor-optimization"></a>Optimisation de plusieurs écran  
 Vous risquez considérablement les performances lorsque le système de rendu déplace un <xref:System.Windows.Interop.D3DImage> vers un autre moniteur.  
  
 Sur WDDM, tant que les analyses sont sur le même vidéo carte et que vous utilisez `Direct3DCreate9Ex`, il n’existe aucune diminution des performances. Si les analyses se trouvent sur des cartes vidéos séparées, les performances sont réduites. Sous Windows XP, les performances sont toujours réduites.  
  
 Lorsque le <xref:System.Windows.Interop.D3DImage> se déplace vers un autre moniteur, vous pouvez créer une surface sur l’adaptateur correspondant pour restaurer de bonnes performances.  
  
 Pour éviter l’altération des performances, écrire du code spécifiquement pour le cas de plusieurs écran. La liste suivante montre une manière d’écrire du code de plusieurs écran.  
  
1.  Rechercher un point de la <xref:System.Windows.Interop.D3DImage> dans l’espace à l’écran avec le `Visual.ProjectToScreen` (méthode).  
  
2.  Utilisez la `MonitorFromPoint` méthode GDI pour rechercher le moniteur qui affiche le point.  
  
3.  Utilisez la `IDirect3D9::GetAdapterMonitor` consiste à trouver la carte Direct3D9 l’analyse sur.  
  
4.  Si l’adaptateur n’est pas le même que l’adaptateur avec la mémoire tampon d’arrière-plan, créez une nouvelle mémoire tampon d’arrière-plan sur le nouveau moniteur et assignez-la à la <xref:System.Windows.Interop.D3DImage> mémoire tampon d’arrière-plan.  
  
> [!NOTE]
>  Si le <xref:System.Windows.Interop.D3DImage> chevauche moniteurs, les performances seront lents, sauf dans le cas de WDDM et `IDirect3D9Ex` sur la même carte. Il n’existe aucun moyen pour améliorer les performances dans ce cas.  
  
 L’exemple de code suivant montre comment rechercher le moniteur actuel.  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 Mettre à jour le moniteur lors de la <xref:System.Windows.Interop.D3DImage> les modifications de taille ou la position du conteneur, ou la mise à jour de l’analyse à l’aide un `DispatcherTimer` qui met à jour plusieurs fois par seconde.  
  
## <a name="wpf-software-rendering"></a>Rendu logiciel WPF  
 WPF restitue de façon synchrone sur le thread d’interface utilisateur dans le logiciel dans les situations suivantes.  
  
-   Impression  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 Lorsqu’une de ces situations se produit, le système de rendu appelle la <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> méthode pour copier la mémoire tampon matérielle dans le logiciel. L’implémentation par défaut appelle la `GetRenderTargetData` méthode avec la surface. Étant donné que cet appel se produit en dehors du modèle de verrouiller/déverrouiller, il risque d’échouer. Dans ce cas, le `CopyBackBuffer` méthode renvoie `null` et aucune image n’est affichée.  
  
 Vous pouvez remplacer le <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> méthode, appelez l’implémentation de base, et si elle retourne `null`, vous pouvez retourner un espace réservé <xref:System.Windows.Media.Imaging.BitmapSource>.  
  
 Vous pouvez également implémenter votre propre rendu logiciel au lieu d’appeler l’implémentation de base.  
  
> [!NOTE]
>  Si WPF est rendu complètement dans le logiciel, <xref:System.Windows.Interop.D3DImage> n’est pas affiché, car WPF ne possède pas un tampon d’affichage.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Interop.D3DImage>  
 [Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)  
 [Procédure pas à pas : création de contenu Direct3D9 à héberger dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)  
 [Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)
