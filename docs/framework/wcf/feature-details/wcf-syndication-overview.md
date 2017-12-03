---
title: Vue d'ensemble de la syndication WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f1595cbb1d225e3dd4e73a354028745d4cd0428
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-syndication-overview"></a>Vue d'ensemble de la syndication WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit la prise en charge pour exposer des flux de syndication depuis un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. La syndication est un mécanisme d'intégration d'application par lequel un serveur expose des données d'application dans un format interopérable appelé « flux ». Un flux est une collection de données d'application incluant des métadonnées (titre, auteur, URL et autres métadonnées) au niveau du flux et une série d'éléments de flux. Dans le flux, les éléments de flux sont habituellement ordonnés par ordre chronologique inverse. Un élément de flux se compose d'un jeu standard de métadonnées au niveau de l'élément (titre, URL, date de création, catégorie et autres métadonnées au niveau de l'élément) et une quantité arbitraire de données d'application spécifiques. Les deux types de flux de syndication les plus communs, RSS 2.0 (Really Simple Syndication) et Atom 1.0, sont tous deux pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="object-model"></a>Modèle objet  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] définit un jeu de classes spécifiques à la syndication qui vous permettent d'utiliser des flux, des éléments de flux et des métadonnées connexes, indépendamment du format : <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink> et d'autres classes spécifiques à la syndication. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]définit également des classes d’infrastructure qui s’appuient sur le modèle de programmation WCF REST pour fournir la prise en charge de syndication, y compris : <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, et <!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>--> `RSS20FeedFormatter`. Les classes du module de formatage du flux prennent en charge la sérialisation du modèle objet depuis et vers RSS 2.0 et Atom 1.0.  
  
## <a name="scenarios"></a>Scénarios  
 Aujourd'hui, la syndication est généralement utilisée pour la création de blogs, où l'auteur du blog publie périodiquement des informations. Il peut s'agir de texte, d'images, de musique ou d'autres types d'informations. De nombreux journaux et magazines publient également des actualités ou des articles en utilisant la syndication. En s'abonnant à ce flux, un utilisateur peut se tenir à jour des nouvelles informations publiées par ces sites. Bien que la syndication soit généralement associée aux blogs et aux éditeurs, elle peut être utilisée avec toute application qui expose une collection d'informations ; par exemple, une base de données des bogues que vous souhaitez exposer à l'aide d'un flux de syndication. Vous pouvez créer un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui expose une opération appelée `CodeDefects`. Cette opération peut prendre un paramètre qui spécifie l'adresse de messagerie de la personne dont vous souhaitez récupérer les bogues. Un client peut utiliser l'URL suivante pour appeler l'opération : http://someserver/bugDatabase/CodeDefects?user=johndoe.  
  
## <a name="syndication-formats"></a>Formats de syndication  
 La plate-forme de syndication [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge RSS 2.0 et Atom 1.0.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
