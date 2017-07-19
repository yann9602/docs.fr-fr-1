---
title: "D&#233;ploiement d&#39;un projet de biblioth&#232;que WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# D&#233;ploiement d&#39;un projet de biblioth&#232;que WCF
Cette rubrique décrit comment déployer un projet de bibliothèque du service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## Déploiement d'une bibliothèque du service WCF  
 Une bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] est une bibliothèque de liens dynamiques \(DLL\).À ce titre, elle ne peut pas être exécutée seule.Elle doit être déployée dans un environnement d'hébergement.Pour plus d'informations sur ce processus, consultez [Hébergement et consommation de services WCF](http://go.microsoft.com/fwlink/?LinkId=99932) \(page pouvant être en anglais\).  
  
 Une bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] peut être déployée comme tout autre service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Sachez toutefois que [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ne prend pas en charge de configuration pour les DLL.<xref:System.Configuration> prend en charge un fichier de configuration par domaine d'application.Le projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] contourne cette limitation en fournissant un fichier App.config pour la bibliothèque pendant la phase de développement.Toutefois, le fichier App.config n'est pas reconnu après le déploiement.  
  
 Vous devez placer votre code de configuration dans le fichier de configuration reconnu par votre environnement d'hébergement.Pour l'auto\-hébergement, vous devez copier le contenu du fichier App.config dans le fichier App.config de l'exécutable d'hébergement.Si vous utilisez IIS pour héberger votre service, vous devez copier le contenu du fichier App.config dans le fichier Web.config du répertoire virtuel.