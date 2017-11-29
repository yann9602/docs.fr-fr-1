---
title: "Utilisation de données binaires (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, binary data
- WCF Data Services, streams
ms.assetid: aeccc45c-d5c5-4671-ad63-a492ac8043ac
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ed6e20e899ce151f91c370bdf9553a7ace23c9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-binary-data-wcf-data-services"></a>Utilisation de données binaires (services de données WCF)
Le [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliothèque cliente vous permet de récupérer et de mettre à jour des données binaires à partir une [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] de flux dans une des manières suivantes :  
  
-   Comme une propriété de type primitif d'entité. Il s'agit de la méthode conseillée lors de l'utilisation de petits objets de données binaires, faciles à charger en mémoire. Dans ce cas, la propriété binaire est une propriété d'entité exposée par le modèle de données, et le service de données sérialise les données binaires sous forme de XML binaire encodé Base 64 dans le message de réponse.  
  
-   Comme un flux distinct de ressources binaires. Ceci est la méthode conseillée pour l'accès et la modification de données d'objet BLOB (binary large object) qui peuvent représenter des photos, des vidéos ou tout autre type de données binaires encodées.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]implémente la diffusion en continu de données binaires à l’aide de HTTP comme défini dans le [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Dans ce mécanisme, des données binaires sont traitées comme une ressource multimédia distincte de mais liées à une entité, qui est appelée une entrée de lien média. Pour plus d’informations, consultez [fournisseur de diffusion en continu](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).  
  
> [!TIP]
>  Pour obtenir un exemple montrant comment créer un [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] application cliente qui télécharge les fichiers image binaires depuis un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service stockant des photos, consultez le billet [données Services de diffusion en continu série fournisseur-partie 2 : l’accès à un support de sauvegarde Flux de ressources à partir du Client](http://go.microsoft.com/fwlink/?LinkId=201637). Pour télécharger l’exemple de code pour le service de données photo flux exposé dans le billet de blog, consultez la [de diffusion en continu de photos données Service exemple](http://go.microsoft.com/fwlink/?LinkId=198988) dans MSDN Code Gallery.  
  
## <a name="entity-metadata"></a>Métadonnées d'entité  
 Une entité qui possède un flux de ressources multimédia lié est signalée dans les métadonnées du service de données par l'attribut `HasStream` appliqué à un type d'entité qui est l'entrée de lien média. Dans l’exemple suivant, la `PhotoInfo` entité est une entrée de lien média qui possède une ressource multimédia associée, indiquée par la `HasStream` attribut.  
  
 [!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria photo streaming service/xml/photodata.edmx#hasstream)]  
  
 Les autres exemples de cette rubrique indiquent comment accéder et modifier le flux de ressources multimédia. Pour obtenir un exemple complet montrant comment consommer un flux de ressources multimédia dans une application cliente .NET Framework à l’aide de la [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliothèque cliente, consultez le billet [l’accès à un flux de ressources multimédia à partir du Client](http://go.microsoft.com/fwlink/?LinkID=201637).  
  
## <a name="accessing-the-binary-resource-stream"></a>Accès au flux de ressources binaires  
 La bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] offre des méthodes pour accéder aux flux de ressources multimédia depuis un service de données basé sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Lors du téléchargement d'une ressource multimédia, vous pouvez utiliser l'URI de la ressource multimédia ou bien vous pouvez obtenir un flux binaire qui contient les données de la ressource multimédia elle-même. Vous pouvez également télécharger les données de la ressource multimédia sous la forme d'un flux binaire.  
  
> [!TIP]
>  Pour obtenir un exemple montrant comment créer un [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] application cliente qui télécharge les fichiers image binaires depuis un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service stockant des photos, consultez le billet [données Services de diffusion en continu série fournisseur-partie 2 : l’accès à un support de sauvegarde Flux de ressources à partir du Client](http://go.microsoft.com/fwlink/?LinkId=201637). Pour télécharger l’exemple de code pour le service de données photo flux exposé dans le billet de blog, consultez la [de diffusion en continu de photos données Service exemple](http://go.microsoft.com/fwlink/?LinkId=198988) dans MSDN Code Gallery.  
  
### <a name="getting-the-uri-of-the-binary-stream"></a>Obtenir l'URI du flux binaire  
 Lorsque vous récupérez certains types de ressources multimédia, tels que des images et d'autres fichiers multimédia, il est souvent plus facile d'utiliser l'URI de la ressource média de votre application que le flux de données binaires lui-même. Pour obtenir l'URI d'un flux de ressources associé à une entrée de lien média donnée, vous devez appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> sur l'instance <xref:System.Data.Services.Client.DataServiceContext> qui suit l'entité. L'exemple suivant illustre comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStreamUri%2A> pour obtenir l'URI d'un flux de ressources multimédia utilisé pour créer une nouvelle image sur le client :  
  
 [!code-csharp[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photowindow.xaml.cs#getreadstreamuri)]
 [!code-vb[Astoria Photo Streaming Client#GetReadStreamUri](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photowindow.xaml.vb#getreadstreamuri)]  
  
### <a name="downloading-the-binary-resource-stream"></a>Téléchargement d'un flux de ressources binaires  
 Lorsque vous récupérez un flux de ressources binaires, vous devez appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> sur l'instance <xref:System.Data.Services.Client.DataServiceContext> qui effectue le suivi de l'entrée de lien média. Cette méthode envoie une demande au service de données qui retourne un objet <xref:System.Data.Services.Client.DataServiceStreamResponse>, lequel possède une référence au flux de données qui contient la ressource. Utilisez cette méthode lorsque votre application nécessite que la ressource binaire soit un <xref:System.IO.Stream>. L'exemple suivant illustre comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> pour récupérer un flux utilisé pour créer une nouvelle image sur le client :  
  
 [!code-csharp[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria streaming client/cs/customerphotowindow.xaml.cs#getreadstreamclient)]
 [!code-vb[Astoria Streaming Client#GetReadStreamClient](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria streaming client/vb/customerphotowindow.xaml.vb#getreadstreamclient)]  
  
> [!NOTE]
>  L'en-tête Content-Length du message de réponse qui contient le flux binaire en continu n'est pas défini par le service de données. Cette valeur ne peut pas refléter la longueur réelle du flux de données binaires en continu.  
  
### <a name="uploading-a-media-resource-as-a-stream"></a>Téléchargement d'une ressource multimédia comme un flux  
 Pour insérer ou mettre à jour une ressource multimédia, appelez la méthode <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> sur l'instance <xref:System.Data.Services.Client.DataServiceContext> qui effectue le suivi de l'entité. Cette méthode envoie une demande au service de données qui contient la ressource multimédia lue depuis le flux de données fourni. L'exemple suivant indique comment appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> pour envoyer une image au service de données :  
  
 [!code-csharp[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria photo streaming client/cs/photodetailswindow.xaml.cs#setsavestream)]
 [!code-vb[Astoria Photo Streaming Client#SetSaveStream](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria photo streaming client/vb/photodetailswindow.xaml.vb#setsavestream)]  
  
 Dans cet exemple, la méthode <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> est appelée en fournissant une valeur `true` pour le paramètre `closeStream`. Cela garantit que l'objet <xref:System.Data.Services.Client.DataServiceContext> ferme le flux de données une fois les données binaires téléchargées sur le service de données.  
  
> [!NOTE]
>  Lorsque vous appelez <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A>, le flux n'est pas transmis au service de données jusqu'à ce que la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> soit appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Liaison de données aux contrôles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)
