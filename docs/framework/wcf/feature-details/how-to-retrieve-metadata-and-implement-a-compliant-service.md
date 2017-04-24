---
title: "Comment&#160;: r&#233;cup&#233;rer des m&#233;tadonn&#233;es et impl&#233;menter un service conforme | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Comment&#160;: r&#233;cup&#233;rer des m&#233;tadonn&#233;es et impl&#233;menter un service conforme
Souvent, la personne qui conçoit et implémente des services n'est pas la même. Dans les environnements où l'interaction d'applications est importante, les contrats peuvent être conçus ou décrits en WSDL (Web Services Description Language) et un développeur doit implémenter un service qui se conforme au contrat fourni. Vous pouvez souhaiter également effectuer une migration d'un service existant vers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mais conserver le format de transmission. De plus, les contrats duplex requièrent que les appelants implémentent également un contrat de rappel.  
  
 Dans ce cas, vous devez utiliser le [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (ou un outil équivalent) pour générer une interface de contrat de service dans un langage managé que vous pouvez implémenter pour répondre aux exigences du contrat. En général, le [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) est utilisé pour acquérir un contrat de service qui est utilisé avec une fabrique de canaux ou un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] type ainsi qu’un fichier de configuration client qui permet de configurer la liaison et l’adresse du client. Pour utiliser le fichier de configuration généré, vous devez le remplacer par un fichier de configuration de service. Vous devrez peut-être aussi modifier le contrat de service.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Pour récupérer des données et implémenter un service conforme  
  
1.  Utilisez le [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) par rapport à un point de terminaison de métadonnées pour générer un fichier de code ou de fichiers de métadonnées.  
  
2.  Recherchez la portion du code du fichier de sortie qui contient l’interface souhaitée (s’il existe plusieurs) qui est marqué avec la <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName> attribut. L’exemple de code suivant montre les deux interfaces générées par [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). La première (`ISampleService`) est l'interface de contrat de service que vous implémentez pour créer un service conforme. La seconde (`ISampleServiceChannel`) est une interface d’assistance destinée au client qui s’étend à la fois l’interface de contrat de service et <xref:System.ServiceModel.IClientChannel?displayProperty=fullName> et doit être utilisée dans une application cliente.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  Si le fichier WSDL ne spécifie pas une action de réponse pour toutes les opérations, les contrats d’opération générés peuvent avoir le <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> propriété définie sur le caractère générique (*). Supprimez ce paramètre de propriété. Sinon, lorsque vous implémentez les métadonnées de contrat de service, celles-ci ne peuvent pas être exportées pour ces opérations.  
  
4.  Implémentez l'interface sur une classe et hébergez le service. Pour obtenir un exemple, consultez [Comment : implémenter un contrat de Service](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), ou consultez une implémentation simple ci-dessous dans la section exemple.  
  
5.  Dans la configuration du client de fichiers qui le [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) génère, modifier le [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) section de configuration à un [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section de configuration. (Pour obtenir un exemple d'un fichier de configuration d'application cliente généré, consultez la section « Exemple » suivante.)  
  
6.  Dans le [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuration en créant un `name` l’attribut dans le [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section de configuration pour votre implémentation de service.  
  
7.  Affectez à l'attribut `name` de service le nom de configuration pour votre implémentation de service.  
  
8.  Ajoutez les éléments de configuration de point de terminaison qui utilisent le contrat de service implémenté à la section de configuration du service.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre la majorité d’un fichier de code généré en exécutant la [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) sur les fichiers de métadonnées.  
  
 L'exemple de code suivant montre :  
  
-   L'interface de contrat de service qui, lorsqu'elle est implémentée, se conforme aux spécifications de contrat (`ISampleService`).  
  
-   L’interface d’assistance destinée au client qui s’étend à la fois l’interface de contrat de service et <xref:System.ServiceModel.IClientChannel?displayProperty=fullName> et doit être utilisée dans une application cliente (`ISampleServiceChannel`).  
  
-   La classe d’assistance qui étend <xref:System.ServiceModel.ClientBase%601?displayProperty=fullName> et doit être utilisée dans une application cliente (`SampleServiceClient`).  
  
-   Le fichier de configuration généré à partir du service.  
  
-   L'implémentation d'un service `ISampleService` simple.  
  
-   Conversion du fichier de configuration côté client vers une version côté service.  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]  
  
 <!-- TODO: review snippet reference [!code[ClientProxyCodeSample#10](../../../../samples/snippets/common/VS_Snippets_CFX/clientproxycodesample/common/client.exe.config#10)]  -->
 <!-- TODO: review snippet reference [!code-csharp[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]  -->  
  
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]  
  
 <!-- TODO: review snippet reference [!code[ClientProxyCodeSample#20](../../../../samples/snippets/common/VS_Snippets_CFX/clientproxycodesample/common/hostapplication.exe.config#20)]  -->
 <!-- TODO: review snippet reference [!code-csharp[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]  -->  
  
## <a name="see-also"></a>Voir aussi  
 [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)