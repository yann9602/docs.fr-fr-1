---
title: "Comment&#160;: sp&#233;cifier le type d&#39;informations d&#39;identification du client | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "informations d'identification de sécurité, ajouter des messages SOAP"
  - "WCF, sécurité"
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: sp&#233;cifier le type d&#39;informations d&#39;identification du client
Après avoir défini un mode de sécurité \(transport ou message\), vous avez pouvez définir le type d'informations d'identification du client.Cette propriété spécifie le type d'informations d'identification que le client doit fournir au service dans le cadre de l'authentification.[!INCLUDE[crabout](../../../includes/crabout-md.md)] la définition du mode de sécurité \(étape nécessaire avant de définir le type d'informations d'identification du client\), consultez [Comment : définir le mode de sécurité](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### Pour définir le type d'informations d'identification du client dans le code  
  
1.  Créez une instance de la liaison que le service utilisera.Cet exemple utilise la liaison <xref:System.ServiceModel.WSHttpBinding>.  
  
2.  Affectez la valeur appropriée à la propriété <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>.Cet exemple utilise le mode de message.  
  
3.  Affectez la valeur appropriée à la propriété <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A>.Dans notre exemple, la propriété est définie de sorte à utiliser l'authentification Windows \(<xref:System.ServiceModel.MessageCredentialType>\).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### Pour définir le type d'informations d'identification du client dans la configuration  
  
1.  Ajoutez un élément [\<system.serviceModel\>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) au fichier de configuration.  
  
2.  Ajoutez un élément [\<liaisons\>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) comme élément enfant.  
  
3.  Ajoutez une liaison appropriée.Cet exemple utilise l'élément [\<wsHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
4.  Ajoutez un élément [\<liaison\>](../../../docs/framework/misc/binding.md), puis affectez à l'attribut `name` une valeur appropriée.Cet exemple utilise le nom « SecureBinding ».  
  
5.  Ajoutez une liaison `<security>`.Affectez la valeur appropriée à l'attribut `mode`.Cet exemple lui affecte la valeur `"Message"`.  
  
6.  Ajoutez un élément `<message>` ou un élément `<transport>` comme requis par le mode de sécurité.Affectez la valeur appropriée à l'attribut `clientCredentialType`.Cet exemple utilise `"Windows"`.  
  
    ```  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## Voir aussi  
 [Sécurisation de services](../../../docs/framework/wcf/securing-services.md)   
 [Comment : définir le mode de sécurité](../../../docs/framework/wcf/how-to-set-the-security-mode.md)