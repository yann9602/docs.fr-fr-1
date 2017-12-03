---
title: "Comment : exposer un contrat à des clients SOAP et Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c04da670c84aaecf3587e6620c70e94c6b7350e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a>Comment : exposer un contrat à des clients SOAP et Web
Par défaut, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] met à disposition les points de terminaison uniquement aux clients SOAP. Dans [Comment : créer un Service WCF Web HTTP de base](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), un point de terminaison est mis à disposition des clients non-SOAP. Dans certains cas, vous pouvez souhaiter rendre le même contrat disponible pour les deux, comme point de terminaison Web et comme point de terminaison SOAP. Cette rubrique explique comment procéder.  
  
### <a name="to-define-the-service-contract"></a>Pour définir le contrat de service  
  
1.  Définissez un contrat de service à l'aide d'une interface marquée avec les attributs <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> et <xref:System.ServiceModel.Web.WebGetAttribute>, comme illustré dans le code suivant.  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Par défaut, <xref:System.ServiceModel.Web.WebInvokeAttribute> mappe des appels POST à l'opération. Toutefois, vous pouvez spécifier la méthode pour mapper à l'opération un paramètre pour "method=". <xref:System.ServiceModel.Web.WebGetAttribute> n'a pas de paramètre « method= » et mappe uniquement des appels GET à l'opération de service.  
  
2.  Implémentez le contrat de service, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a>Pour héberger le service  
  
1.  Créez un objet <xref:System.ServiceModel.ServiceHost>, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  Ajoutez un <xref:System.ServiceModel.Description.ServiceEndpoint> avec <xref:System.ServiceModel.BasicHttpBinding> pour le point de terminaison SOAP, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  Ajoutez un <xref:System.ServiceModel.Description.ServiceEndpoint> avec <xref:System.ServiceModel.WebHttpBinding> pour le point de terminaison non-SOAP et ajoutez le <xref:System.ServiceModel.Description.WebHttpBehavior> au point de terminaison, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  Appelez `Open()` sur une instance <xref:System.ServiceModel.ServiceHost> pour ouvrir l'hôte du service, comme illustré dans le code suivant.  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a>Pour appeler des opérations de service mappées à GET dans Internet Explorer  
  
1.  Ouvrez Internet Explorer et tapez «`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`» et appuyez sur ENTRÉE. L'URL contient l'adresse de base du service ("http://localhost:8000/"), l'adresse relative du point de terminaison (""), l'opération de service à appeler ("EchoWithGet") et un point d'interrogation suivi d'une liste de paramètres séparés par une esperluette (&).  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a>Pour appeler des opérations de service sur le point de terminaison Web dans le code  
  
1.  Créez une instance de <xref:System.ServiceModel.Web.WebChannelFactory%601> au sein d'un bloc `using`, comme illustré dans le code suivant.  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  `Close()` est automatiquement appelé sur le canal à la fin du bloc `using`.  
  
1.  Créez le canal, puis appelez le service, comme illustré dans le code suivant.  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a>Pour appeler des opérations de service sur le point de terminaison SOAP  
  
1.  Créez une instance de <xref:System.ServiceModel.ChannelFactory> au sein d'un bloc `using`, comme illustré dans le code suivant.  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  Créez le canal, puis appelez le service, comme illustré dans le code suivant.  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a>Pour fermer l'hôte de service  
  
1.  Fermez l'hôte de service comme illustré dans le code suivant.  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a>Exemple  
 Les éléments suivants représentent l'intégralité du code pour cette rubrique.  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Lors de la compilation de Service.cs, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
