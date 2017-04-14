---
title: "Comment&#160;: auditer les &#233;v&#233;nements de s&#233;curit&#233; relatifs &#224; Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sécurité [WCF], audit d'événements"
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: 19
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 19
---
# Comment&#160;: auditer les &#233;v&#233;nements de s&#233;curit&#233; relatifs &#224; Windows Communication Foundation
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet d'enregistrer des événements de sécurité dans le journal des événement Windows, qui peut être affiché à l'aide de l'Observateur d'événements Windows.  Cette rubrique explique comment installer une application afin qu'elle enregistre des événements de sécurité.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Audit de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### Pour auditer des événements de sécurité dans le code  
  
1.  Spécifiez l'emplacement du journal d'audit.  Pour cela, affectez à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> de la classe <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> l'une des valeurs d'énumération <xref:System.ServiceModel.AuditLogLocation>, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     L'énumération <xref:System.ServiceModel.AuditLogLocation> a trois valeurs : `Application`,  `Security` ou `Default`.  La valeur spécifie l'un des journaux visibles dans l'Observateur d'événements, le journal de sécurité ou le journal des applications.  Si vous utilisez la valeur `Default`, le journal réel dépend du système d'exploitation sur lequel l'application s'exécute.  Si l'audit est activé et que l'emplacement du journal n'est pas spécifié, la valeur par défaut est le journal `Security` pour les plateformes qui prennent en charge l'écriture dans le journal de sécurité ; sinon, les événements sont consignés dans le journal `Application`.  Seuls [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] et [!INCLUDE[wv](../../../../includes/wv-md.md)] prennent en charge l'écriture dans le journal de sécurité par défaut.  
  
2.  Installez les types d'événements à auditer.  Vous pouvez auditer simultanément des événements au niveau du service ou des événements d'autorisation au niveau du message.  Pour cela, affectez à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> ou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> l'une des valeurs d'énumération <xref:System.ServiceModel.AuditLevel>, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Spécifiez s'il convient de supprimer ou d'exposer les défaillances de l'application concernant des événements d'audit de journal.  Affectez à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> la valeur `true` ou `false`, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     La propriété `SuppressAuditFailure` par défaut a la valeur `true`, afin que l'échec de l'audit n'affecte pas l'application.  Sinon, une exception est levée.  Tout audit exécuté avec succès entraîne l'écriture d'un suivi de détails d'information.  Tout échec d'audit entraîne l'écriture d'un suivi au niveau d'erreur.  
  
4.  Supprimez le <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> existant de la collection de comportements située dans la description d'un <xref:System.ServiceModel.ServiceHost>.  La collection de comportements est accessible par le biais de la propriété <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, qui elle\-même est accessible à partir de la propriété <xref:System.ServiceModel.ServiceHostBase.Description%2A>.  Puis, ajoutez le nouveau <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à la même collection, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### Pour installer l'audit dans la configuration  
  
1.  Pour installer l'audit dans la configuration, ajoutez un élément [\<comportement\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) à la section [\<comportements\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) du fichier web.config.  Puis, ajoutez un élément [\<serviceSecurityAudit\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) et définissez les différents attributs, tel qu'indiqué dans l'exemple suivant.  
  
    ```  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"   
                serviceAuthorizationAuditLevel="None"   
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2.  Vous devez spécifier le comportement du service, tel qu'indiqué dans l'exemple suivant.  
  
    ```  
    <services>  
        <service type="WCS.Samples.Service.Echo"   
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"   
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
  
    ```  
  
## Exemple  
 Le code suivant crée une instance de la classe <xref:System.ServiceModel.ServiceHost> et ajoute un nouveau <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> à sa collection de comportements.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## Sécurité .NET Framework  
 Affecter à la propriété <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> la valeur `true` supprime toute impossibilité de générer des audits de sécurité \(si la propriété a la valeur `false`, une exception est levée\).  Toutefois, si vous activez la propriété Windows **Paramètre de sécurité locale** suivante, tout échec de génération d'événements d'audit provoque l'arrêt immédiat de Windows :  
  
 **Audit : arrêter immédiatement le système s'il n'est pas possible de se connecter aux audits de sécurité**  
  
 Pour définir la propriété, ouvrez la boîte de dialogue **Paramètres de sécurité locaux**.  Sous **Paramètres de sécurité**, cliquez sur **Stratégies locales**.  Puis, cliquez sur **Options de sécurité**.  
  
 Si la propriété <xref:System.ServiceModel.AuditLogLocation> a la valeur <xref:System.ServiceModel.AuditLogLocation> et que le paramètre **Auditer l'accès aux objets** n'est pas défini dans la **Stratégie de sécurité locale**, les événements d'audit ne seront pas écrits dans le journal de sécurité.  Notez qu'aucun échec n'est retourné, mais que les entrées d'audit ne sont pas écrites dans le journal de sécurité.  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>   
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>   
 <xref:System.ServiceModel.AuditLogLocation>   
 [Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)