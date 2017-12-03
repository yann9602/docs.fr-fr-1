---
title: "Exceptions d'hébergement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cfbe5fa9944b97704f153e9b38229ddfd28a9c5d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-exceptions"></a>Exceptions d'hébergement
Cette rubrique répertorie toutes les exceptions générées par l'hébergement.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|L'URI complet n'est pas autorisé. Les URI complets ne sont pas pris en compte pour l'API ServiceHostingEnvironment.EnsureServiceAvailable. Utilisez un chemin d'accès virtuel pour le service correspondant.|  
|Hosting_BuildProviderCouldNotCreateType|Le type CLR spécifié ne peut pas être chargé pendant la compilation de service. Vérifiez que ce type n’est défini dans un fichier source situé dans l’application \\répertoire \App_Code, contenu dans un assembly compilé situé dans l’application \\\bin répertoire, ou qu’il est présent dans un assembly installé dans le Global Assembly Cache. Le nom du type respecte la casse. Les répertoires comme \\\App_Code et \\\bin doit se trouver dans le répertoire racine de l’application. Le \\\App_Code et \\\bin répertoires ne peuvent pas être imbriqués dans des sous-répertoires.|
