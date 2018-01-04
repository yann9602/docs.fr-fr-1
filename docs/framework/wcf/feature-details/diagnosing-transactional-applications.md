---
title: "Diagnostic d’applications transactionnelles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0826881bac88f2bfa933ae71b798186dafc55303
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-transactional-applications"></a>Diagnostic d’applications transactionnelles
Cette rubrique décrit comment utiliser la fonctionnalité de diagnostic et de gestion [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour dépanner une application transactionnelle.  
  
## <a name="performance-counters"></a>Compteurs de performance  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un jeu standard de compteurs de performance vous permettant de mesurer la performance de votre application transactionnelle. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Les compteurs de performance](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Les compteurs de performance sont définis à trois niveaux différents : service, point de terminaison et opération, tel que décrit dans les tableaux suivants.  
  
### <a name="service-performance-counters"></a>Compteurs de performance de service  
  
|Compteur de performance|Description|  
|-------------------------|-----------------|  
|Transactions passées|Nombre de transactions passées aux opérations dans ce service. Ce compteur est incrémenté chaque fois qu'une transaction est présente dans le message envoyé au service.|  
|Transactions passées par seconde|Nombre de transactions passées aux opérations dans ce service par seconde. Ce compteur est incrémenté chaque fois qu'une transaction est présente dans le message envoyé au service.|  
|Opérations traitées validées|Nombre d'opérations traitées avec des résultats validés dans ce service. Le travail effectué dans le cadre de telles opérations a été entièrement validé. Les ressources sont mises à jour en fonction du travail effectué dans l'opération.|  
|Opérations traitées validées par seconde|Nombre d'opérations traitées avec des résultats validés dans ce service par seconde. Le travail effectué dans le cadre de telles opérations a été entièrement validé. Les ressources sont mises à jour en fonction du travail effectué dans l'opération.|  
|Opérations traitées annulées|Nombre d'opérations traitées avec des résultats annulés dans ce service. Le travail effectué dans le cadre de telles opérations est annulé. Les ressources sont replacées à leur état antérieur.|  
|Nombre d'opérations traitées abandonnées par seconde|Nombre d'opérations traitées avec des résultats annulés dans ce service par seconde. Le travail effectué dans le cadre de telles opérations est annulé. Les ressources sont replacées à leur état antérieur.|  
|Opérations traitées avec des résultats incertains|Nombre d'opérations traitées avec des résultats incertains dans ce service. L'état d'un travail effectué avec un résultat incertain est indéterminé. Les ressources sont conservées dans l'attente des résultats.|  
|Opérations traitées avec des résultats incertains par seconde|Nombre d'opérations traitées avec des résultats incertains dans ce service par seconde. L'état d'un travail effectué avec un résultat incertain est indéterminé. Les ressources sont conservées dans l'attente des résultats.|  
  
### <a name="endpoint-performance-counters"></a>Compteurs de performance de point de terminaison  
  
|Compteur de performance|Description|  
|-------------------------|-----------------|  
|Transactions passées|Nombre de transactions passées à des opérations au niveau de ce point de terminaison. Ce compteur est incrémenté chaque fois qu'une transaction est présente dans le message envoyé au point de terminaison.|  
|Transactions passées par seconde|Nombre de transactions passées à des opérations au niveau de ce point de terminaison par seconde. Ce compteur est incrémenté chaque fois qu'une transaction est présente dans le message envoyé au point de terminaison.|  
  
### <a name="operation-performance-counters"></a>Compteurs de performance d'opération  
  
|Compteur de performance|Description|  
|-------------------------|-----------------|  
|Transactions passées|Nombre de transactions passées à des opérations au niveau de ce point de terminaison. Ce compteur est incrémenté chaque fois qu'une transaction est présente dans le message envoyé au point de terminaison.|  
|Transactions passées par seconde|Nombre de transactions passées à des opérations au niveau de ce point de terminaison par seconde. Ce compteur est incrémenté chaque fois qu'une transaction est présente dans le message envoyé au point de terminaison.|  
  
## <a name="windows-management-instrumentation"></a>Windows Management Instrumentation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expose au moment de l'exécution les données d'inspection d'un service par l'intermédiaire d'un fournisseur WMI (Windows Management Instrumentation) de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]l’accès aux données WMI, consultez [à l’aide de Windows Management Instrumentation pour les Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Un certain nombre de propriétés WMI en lecture seule indiquent les paramètres de transaction appliqués pour un service. Les tableaux suivants répertorient l'ensemble de ces paramètres.  
  
 Sur un service, `ServiceBehaviorAttribute` a les propriétés suivantes :  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Booléen|Spécifie si l'objet de service est recyclé lorsque la transaction actuelle se termine.|  
|TransactionAutoCompleteOnSessionClose|Booléen|Spécifie si les transactions en attente sont complétées lorsque la session actuelle se ferme.|  
|TransactionIsolationLevel|Chaîne contenant une valeur valide de l'énumération <xref:System.Transactions.IsolationLevel>.|Spécifie le niveau d'isolation des transactions que ce service prend en charge.|  
|TransactionTimeout|<xref:System.DateTime>|Spécifie le délai dans lequel une transaction doit se terminer.|  
  
 `ServiceTimeoutsBehavior` a la propriété suivante :  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|Spécifie le délai dans lequel une transaction doit se terminer.|  
  
 Sur une liaison, `TransactionFlowBindingElement` a les propriétés suivantes :  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|TransactionProtocol|Chaîne contenant une valeur valide du type <xref:System.ServiceModel.TransactionProtocol>.|Spécifie le protocole de transaction utilisé dans le passage d'une transaction.|  
|Liaison|Booléen|Spécifie si le flux de transaction entrant est activé.|  
  
 Sur une opération, `OperationBehaviorAttribute` a les propriétés suivantes :  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Booléen|Spécifie s'il convient de valider automatiquement la transaction actuelle si aucune exception non traitée ne se produit.|  
|TransactionScopeRequired|Booléen|Spécifie si l'opération requiert une transaction.|  
  
 Sur une opération, `TransactionFlowAttribute` a les propriétés suivantes :  
  
|Nom|Type|Description|  
|----------|----------|-----------------|  
|TransactionFlowOption|Chaîne contenant une valeur valide de l'énumération <xref:System.ServiceModel.TransactionFlowOption>.|Spécifie l'étendue à laquelle le flux de transaction est requis.|  
  
## <a name="tracing"></a>Traçage  
 Les suivis vous permettent de surveiller et d'analyser les erreurs dans vos applications transactionnelles. Pour activer le suivi, procédez comme suit :  
  
-   Suivi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standard  
  
     Ce type de suivi est identique à celui des applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Configuration du traçage](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   Suivi WS-AtomicTransaction  
  
     Le suivi de WS-AtomicTransaction peut être activé à l’aide de la [l’utilitaire de Configuration WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Un suivi de ce type permet de connaître l’état des transactions et des participants d’un système. Pour activer également le suivi du modèle de service interne, affectez une valeur valide de l'énumération `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` à la clé de registre <xref:System.Diagnostics.SourceLevels>. Vous pouvez activer la journalisation des messages de la même façon que pour les autres applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Suivi `System.Transactions`  
  
     Lorsque vous utilisez le protocole OleTransactions, les messages de protocole ne peuvent pas être suivis. La prise en charge du suivi fournie par l'infrastructure <xref:System.Transactions> (laquelle utilise OleTransactions) permet aux utilisateurs de consulter les événements qui se sont produits au niveau des transactions. Pour activer le suivi d'une application <xref:System.Transactions>, incluez le code suivant dans le fichier de configuration `App.config`.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     Cela active par ailleurs le suivi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], car [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise également l'infrastructure <xref:System.Transactions>.  
  
## <a name="see-also"></a>Voir aussi  
 [Administration et diagnostics](../../../../docs/framework/wcf/diagnostics/index.md)  
 [Configuration du suivi](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
