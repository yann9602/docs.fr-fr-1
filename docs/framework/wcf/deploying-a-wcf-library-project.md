---
title: "Déploiement d'un projet de bibliothèque WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbddd99125e8615640ca39d091e92cdde87c9faf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-a-wcf-library-project"></a>Déploiement d'un projet de bibliothèque WCF
Cette rubrique décrit comment déployer un projet de bibliothèque du service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="deploying-a-wcf-service-library"></a>Déploiement d'une bibliothèque du service WCF  
 Une bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est une bibliothèque de liens dynamiques (DLL). À ce titre, elle ne peut pas être exécutée seule. Elle doit être déployée dans un environnement d'hébergement. Pour plus d’informations sur ce processus, consultez [hébergement et utilisation des Services WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Une bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut être déployée comme tout autre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]. Sachez toutefois que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ne prend pas en charge de configuration pour les DLL. <xref:System.Configuration> prend en charge un fichier de configuration par domaine d'application. Le projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contourne cette limitation en fournissant un fichier App.config pour la bibliothèque pendant la phase de développement. Toutefois, le fichier App.config n'est pas reconnu après le déploiement.  
  
 Vous devez placer votre code de configuration dans le fichier de configuration reconnu par votre environnement d'hébergement. Pour l'auto-hébergement, vous devez copier le contenu du fichier App.config dans le fichier App.config de l'exécutable d'hébergement. Si vous utilisez IIS pour héberger votre service, vous devez copier le contenu du fichier App.config dans le fichier Web.config du répertoire virtuel.
