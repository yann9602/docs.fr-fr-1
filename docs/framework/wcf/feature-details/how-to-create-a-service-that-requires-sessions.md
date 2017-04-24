---
title: "Comment&#160;: cr&#233;er un service qui requiert des sessions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er un service qui requiert des sessions
Les sessions créent un état partagé entre deux ou plusieurs points de terminaison activant des fonctionnalités utiles telles que les rappels, la sécurité en cascade et des associations entre clients et instances de service. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sessions [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] les applications, consultez [à l’aide de Sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>Pour spécifier qu’un contrat requiert que sa liaison prenne en charge des sessions  
  
1.  Créez un contrat de service qui contient au moins une opération. Pour obtenir un exemple montrant comment créer un contrat de service, consultez [Comment : définir un contrat de Service](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Modifier la <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName> qui déclare le contrat en définissant le <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=fullName> propriété :  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName> si ce contrat doit être exécuté dans une session.  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName> si ce contrat peut être exécuté dans une session.  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName> si ce contrat ne doit pas être exécuté dans une session.  
  
3.  Configurez votre point de terminaison de service pour utiliser une liaison qui prend en charge des sessions. L’exemple de configuration suivant montre l’utilisation de la <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName>, qui prend en charge un WS`-`ReliableMessaging session.  
  
     <!-- TODO: review snippet reference [!code[SCA.Session#2](../../../../samples/snippets/common/VS_Snippets_CFX/sca.session/common/hostapplication.exe.config#2)]  -->
     <!-- TODO: review snippet reference [!code-csharp[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]  -->
     <!-- TODO: review snippet reference [!code-vb[SCA.Session#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/hostapplication.exe.config#2)]  -->  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment spécifier une exigence de session au niveau du contrat et utiliser un fichier de configuration pour prendre en charge cette spécification avec le <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName> liaison.  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]  
  
 <!-- TODO: review snippet reference [!code[SCA.Session#2](../../../../samples/snippets/common/VS_Snippets_CFX/sca.session/common/hostapplication.exe.config#2)]  -->
 <!-- TODO: review snippet reference [!code-csharp[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]  -->
 <!-- TODO: review snippet reference [!code-vb[SCA.Session#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/hostapplication.exe.config#2)]  -->  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>   
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.SessionMode?displayProperty=fullName>