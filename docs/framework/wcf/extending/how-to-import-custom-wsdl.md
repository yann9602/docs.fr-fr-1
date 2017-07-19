---
title: "Comment&#160;: importer un fichier WSDL personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: importer un fichier WSDL personnalis&#233;
Cette rubrique décrit comment importer un fichier WSDL personnalisé.  Pour gérer le fichier WSDL personnalisé, vous devez implémenter l'interface <xref:System.ServiceModel.Description.IWsdlImportExtension>.  
  
### Pour importer le fichier WSDL personnalisé  
  
1.  Implémentez <xref:System.ServiceModel.Description.IWsdlImportExtension>.  Implémentez la méthode <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> pour modifier les métadonnées avant qu'elles ne soient importées.  Implémentez les méthodes <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> et <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> pour modifier les contrats et points de terminaison importés des métadonnées.  Pour accéder au contrat ou point de terminaison importé, utilisez l'objet de contexte correspondant \(<xref:System.ServiceModel.Description.WsdlContractConversionContext> ou <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>\) :  
  
    ```  
    public class WsdlDocumentationImporter : IWsdlImportExtension  
       {  
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
       }  
    ```  
  
2.  Configurez l'application cliente pour utiliser l'importateur WSDL personnalisé.  Notez que si vous utilisez Svcutil.exe, vous devez ajouter la configuration suivante au fichier de configuration de Svcutil.exe \(Svcutil.exe.config\) :  
  
    ```  
    <system.serviceModel>  
          <client>  
            <endpoint   
              address="http://localhost:8000/Fibonacci"   
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
  
    ```  
  
3.  Créez une instance <xref:System.ServiceModel.Description.WsdlImporter> \(en passant l'instance <xref:System.ServiceModel.Description.MetadataSet> qui contient les documents WSDL à importer\), puis appelez <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> :  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
  
    ```  
  
## Voir aussi  
 [Métadonnées](../../../../docs/framework/wcf/feature-details/metadata.md)   
 [Exportation et importation de métadonnées](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)   
 [Publication WSDL personnalisée](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)