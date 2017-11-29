---
title: '&lt;serviceSecurityAudit&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f0c708c19761f6086e1b5c2fdd15904c76fe3de9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicesecurityauditgt"></a>&lt;serviceSecurityAudit&gt;
Spécifie des paramètres qui activent l'audit d'événements de sécurité pendant des opérations de service.  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<serviceSecurityAudit >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessAndFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessAndFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|auditLogLocation|Spécifie l'emplacement du journal d'audit. Les valeurs valides sont les suivantes :<br /><br /> -Valeur par défaut : Événements de sécurité sont écrits dans le journal des applications sur Windows XP et dans le journal des événements sur Windows Server 2003 et Windows Vista.<br />-Application : Les événements d’Audit sont écrits dans le journal des événements.<br />-Security : Les événements d’Audit sont écrits dans le journal des événements de sécurité.<br /><br /> La valeur par défaut est Default. Pour plus d'informations, consultez <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Valeur booléenne qui spécifie le comportement permettant de supprimer les erreurs d'écriture dans le journal d'audit.<br /><br /> Les applications doivent être averties des erreurs d'écriture dans le journal d'audit. Si votre application n'est pas conçue pour gérer les erreurs d'audit, vous devez utiliser cet attribut pour supprimer les erreurs d'écriture dans le journal d'audit.<br /><br /> Si cet attribut a pour valeur `true`, les exceptions autres qu'OutOfMemoryException, StackOverFlowException, ThreadAbortException et ArgumentException qui résultent de tentatives d'écriture d'événements d'audit sont contrôlées par le système et ne sont pas propagées dans l'application. Si cet attribut a pour valeur `false`, toutes les exceptions qui résultent de tentatives d'écriture d'événements d'audit sont passées à l'application.<br /><br /> La valeur par défaut est `true`.|  
|serviceAuthorizationAuditLevel|Spécifie les types d'événements d'autorisation enregistrés dans le journal d'audit. Les valeurs valides sont les suivantes :<br /><br /> -None : Aucun audit d’événements d’autorisation de service est effectuée.<br />-Réussite : Seuls les événements d’autorisation service réussis sont audités.<br />-Failure : Seuls les événements d’autorisation de service échec sont audités.<br />-SuccessAndFailure : Les événements d’autorisation du service réussite et d’échec sont audités.<br /><br /> La valeur par défaut est None. Pour plus d'informations, consultez <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Spécifie le type d'événements d'audit d'authentification de message enregistrés. Les valeurs valides sont les suivantes :<br /><br /> -None : Aucun événement d’audit est générées.<br />-Réussite : Uniquement événements de sécurité (validation complète y compris la validation de signature de message, le chiffrement et validation du jeton) réussis sont enregistrés.<br />-Failure : Seuls les événements d’échec sont enregistrés.<br />-SuccessAndFailure : Les événements de réussite et d’échec sont enregistrés.<br /><br /> La valeur par défaut est None. Pour plus d'informations, consultez <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Remarques  
 Cet élément de configuration sert à effectuer un audit des événements d'authentification [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]. Lorsque l'audit est activé, il est possible de réaliser l'audit des tentatives d'authentification réussies ou échouées (ou les deux). Les événements sont écrits dans l'un des trois journaux des événements : application, sécurité ou journal par défaut de la version du système d'exploitation. Les journaux des événements peuvent être consultés à l'aide de l'Observateur d'événements Windows.  
  
 Pour obtenir un exemple détaillé de l’utilisation de cet élément de configuration, consultez [comportement de l’audit du Service](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Par défaut, sur Windows XP, les événements d’audit peuvent être consultés dans le journal des applications, tandis que sur Windows Server 2003 et Windows Vista, ils peuvent être consultés dans le journal de sécurité. L'emplacement des événements d'audit peut être spécifié en affectant la valeur 'Application' ou 'Security' à l'attribut `auditLogLocation`. Pour plus d’informations, consultez [Comment : auditer les événements de sécurité](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Si les événements sont écrits dans le journal de sécurité, LocalSecurityPolicy-> Enable Object Access doit être défini sur « Success » et « Failure ».  
  
 Lors de la consultation du journal des événements, la source des événements d'audit est « ServiceModel Audit 3.0.0.0 ». Les enregistrements de l'audit d'authentification du message portent la catégorie « MessageAuthentication », tandis que les enregistrements de l'audit d'autorisation du service portent la catégorie « ServiceAuthorization ».  
  
 Les événements de l'audit d'authentification du message permettent de savoir si le message a été falsifié, s'il a expiré et si le client peut s'authentifier auprès du service. Ils fournissent des informations sur la réussite ou l'échec de l'authentification, l'identité du client, le point de terminaison auquel le message a été envoyé et l'action associée au message.  
  
 Les événements de l'audit d'autorisation du service permettent de connaître la décision d'autorisation prise par un gestionnaire d'autorisation du service. Ils fournissent des informations sur la réussite ou l'échec de l'autorisation, l'identité du client, le point de terminaison auquel le message a été envoyé, l'action associée au message, l'identificateur du contexte d'autorisation généré à partir du message entrant et le type du gestionnaire d'autorisations qui a pris la décision d'accès.  
  
## <a name="example"></a>Exemple  
  
```xml  
<system.serviceModel>  
   <serviceBehaviors>  
      <behavior name="NewBehavior">  
         <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
      </behavior>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 [Comportements de sécurité](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [L’audit](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Comment : auditer les événements de sécurité](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [Comportement de l’audit de service](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
