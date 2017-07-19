---
title: "Comment&#160;: &#233;crire une extension pour le ServiceContractGenerator | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Comment&#160;: &#233;crire une extension pour le ServiceContractGenerator
Cette rubrique décrit comment écrire une extension pour le <xref:System.ServiceModel.Description.ServiceContractGenerator>.Cela peut être fait en implémentant l'interface <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> sur un comportement d'opération ou en implémentant l'interface <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> sur un comportement de contrat.Cette rubrique indique comment implémenter l'interface <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> sur un comportement du contrat.  
  
 Le <xref:System.ServiceModel.Description.ServiceContractGenerator> génère des contrats de service, des types de clients et des configurations clientes à partir d'instances <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription> et <xref:System.ServiceModel.Channels.Binding>.En général, vous importez des instances <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription> et <xref:System.ServiceModel.Channels.Binding> à partir de métadonnées de service, puis vous utilisez ces instances pour générer du code pour appeler le service.Dans cet exemple, une implémentation <xref:System.ServiceModel.Description.IWsdlImportExtension> est utilisée pour traiter les annotations WSDL puis ajouter des extensions de génération de code aux contrats importés afin de produire des commentaires sur le code généré.  
  
### Pour écrire une extension pour le ServiceContractGenerator  
  
1.  Implémentez <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.Pour modifier le contrat de service généré, utilisez l'instance <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passée dans la méthode <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  Implémentez <xref:System.ServiceModel.Description.IWsdlImportExtension> sur la même classe.La méthode <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> peut traiter une extension WSDL spécifique \(annotations WSDL dans ce cas\) en ajoutant une extension de génération de code à l'instance <xref:System.ServiceModel.Description.ContractDescription> importée.  
  
    ```  
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
       {  
                // Contract documentation  
             if (context.WsdlPortType.Documentation != null)  
             {  
                    context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
             }  
             // Operation documentation  
             foreach (Operation operation in context.WsdlPortType.Operations)  
             {  
                if (operation.Documentation != null)  
                {  
                   OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
                   if (operationDescription != null)  
                   {  
                            operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
                   }  
                }  
             }  
          }  
          public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)   
            {  
                Console.WriteLine("BeforeImport called.");  
            }  
  
          public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)   
            {  
                Console.WriteLine("ImportEndpoint called.");  
            }  
    ```  
  
3.  Ajoutez l'importateur WSDL à votre configuration cliente :  
  
    ```  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  Dans le code client, créez un `MetadataExchangeClient` et appelez `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  Créez un `WsdlImporter` et appelez `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  Créez un `ServiceContractGenerator` et appelez `GenerateServiceContractType` pour chaque contrat.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> est appelée automatiquement pour chaque comportement de contrat sur un contrat donné qui implémente <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.Cette méthode peut ensuite modifier le <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passé.Dans cet exemple les commentaires sont ajoutés.  
  
## Voir aussi  
 [Métadonnées](../../../../docs/framework/wcf/feature-details/metadata.md)   
 [Comment : importer un fichier WSDL personnalisé](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)