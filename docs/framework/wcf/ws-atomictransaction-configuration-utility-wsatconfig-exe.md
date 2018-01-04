---
title: Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adb44bfee98d01594c9babcf19e19fbf11ba3878
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)
L'utilitaire de configuration WS-AtomicTransaction permet de configurer les paramètres de prise en charge WS-AtomicTransaction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Notes  
 Cet outil de ligne de commande peut être utilisé pour configurer les paramètres WS-AT de base sur un ordinateur local uniquement. Si vous devez configurer les paramètres sur les ordinateurs locaux et distants, vous devez utiliser le composant logiciel enfichable MMC, comme décrit dans [configuration prise en charge de WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 L'outil de ligne de commande se trouve généralement dans le répertoire d'installation du Kit de développement logiciel Windows.  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 Si vous utilisez [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], vous devez télécharger une mise à jour avant d'exécuter WsatConfig.exe. Pour plus d’informations sur cette mise à jour, consultez [mise à jour pour Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) et [disponibilité de Windows XP COM + Hotfix Rollup Package 13](http://go.microsoft.com/fwlink/?LinkId=95341).  
  
 Le tableau suivant affiche les options qui peuvent être utilisées avec l'utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
>  Lorsque vous définissez un certificat SSL pour un port sélectionné, vous remplacez le certificat SSL d’origine associé à ce port, le cas échéant.  
  
|Options|Description|  
|-------------|-----------------|  
|-comptes :\<compte >|Spécifie la liste des comptes, séparés par une virgule, qui peuvent participer à WS-AtomicTransaction. La validation de ces comptes n'est pas vérifiée.|  
|-accountsCerts :\<thumb > &#124; » Émetteur\NomSujet », >|Spécifie la liste des certificats, séparés par une virgule, qui peuvent participer à WS-AtomicTransaction. Les certificats sont indiqués par empreinte numérique ou par la paire Issuer\SubjectName. Utilisez{EMPTY} pour le nom de sujet, s'il est vide.|  
|-endpointCert : < ordinateur &#124; \<thumb > &#124; » Issuer\SubjectName » >|Utilise le certificat d'ordinateur ou un autre certificat de point de terminaison local spécifié par l'empreinte numérique ou par la paire Issuer\SubjectName. Utilise {EMPTY} pour le nom de sujet, s'il est vide.|  
|-maxTimeout :\<s >|Spécifie le délai d'attente maximal, exprimé en secondes. Les valeurs valides vont de 0 à 3 600.|  
|-réseau :\<Activer &#124; désactiver >|Active ou désactive la gestion réseau WS-AtomicTransaction.|  
|-port :\<portNum >|Définit le port HTTPS pour WS-AtomicTransaction.<br /><br /> Si vous avez déjà activé le pare-feu avant d'exécuter cet outil, le port est enregistré automatiquement dans la liste d'exceptions. Si le pare-feu est désactivé avant l'exécution de cet outil, aucun élément supplémentaire n'est configuré concernant le pare-feu.<br /><br /> Si vous activez le pare-feu après avoir configuré WS-AT, vous devez exécuter de nouveau cet outil et fournir le numéro de port à l'aide de ce paramètre. Si vous désactivez le pare-feu après la configuration, WS-AT continue à fonctionner sans entrée supplémentaire.|  
|-timeout :\<s >|Spécifie le délai d'attente par défaut, exprimé en secondes. Les valeurs valides sont comprises entre 1et 3 600.|  
|-traceActivity :\<Activer &#124; désactiver >|Active ou désactive le suivi d'événements d'activité.|  
|-traceLevel :\<Off &#124; Erreur &#124; Critique &#124; Avertissement &#124; informations &#124; Verbose &#124; Tous les >}|Spécifie le niveau de suivi.|  
|-tracePII :\<Activer &#124; désactiver >|Active ou désactive le suivi des informations d'identification personnelle.|  
|-traceProp :\<Activer &#124; désactiver >|Active ou désactive le suivi d'événements de propagation.|  
|-restart|Redémarre MSDTC pour activer immédiatement les modifications apportées. Si cette option n'est pas spécifiée, les modifications entrent en vigueur lorsque MSDTC est redémarré.|  
|-show|Affiche les paramètres actuels du protocole WS-AtomicTransaction.|  
|serveur virtuel- :\<serveur virtuel >|Spécifie le nom du cluster de ressource DTC.|  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [Configuration de la prise en charge WS-Atomic Transaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
