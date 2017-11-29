---
title: "Comment : importer un fichier WSDL personnalisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 00a845fe5c8321d521fb7baa3b16bd009fc3e660
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="0f669-102">Comment : importer un fichier WSDL personnalisé</span><span class="sxs-lookup"><span data-stu-id="0f669-102">How to: Import Custom WSDL</span></span>
<span data-ttu-id="0f669-103">Cette rubrique décrit comment importer un fichier WSDL personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0f669-103">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="0f669-104">Pour gérer le fichier WSDL personnalisé, vous devez implémenter l'interface <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="0f669-104">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="0f669-105">Pour importer le fichier WSDL personnalisé</span><span class="sxs-lookup"><span data-stu-id="0f669-105">To import custom WSDL</span></span>  
  
1.  <span data-ttu-id="0f669-106">Implémentez <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span><span class="sxs-lookup"><span data-stu-id="0f669-106">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="0f669-107">Implémentez la méthode <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> pour modifier les métadonnées avant qu'elles ne soient importées.</span><span class="sxs-lookup"><span data-stu-id="0f669-107">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="0f669-108">Implémentez les méthodes <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> et <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> pour modifier les contrats et points de terminaison importés des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0f669-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="0f669-109">Pour accéder au contrat ou point de terminaison importé, utilisez l'objet de contexte correspondant (<xref:System.ServiceModel.Description.WsdlContractConversionContext> ou <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>) :</span><span class="sxs-lookup"><span data-stu-id="0f669-109">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
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
  
2.  <span data-ttu-id="0f669-110">Configurez l'application cliente pour utiliser l'importateur WSDL personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0f669-110">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="0f669-111">Notez que si vous utilisez Svcutil.exe, vous devez ajouter la configuration suivante au fichier de configuration de Svcutil.exe (Svcutil.exe.config) :</span><span class="sxs-lookup"><span data-stu-id="0f669-111">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
    ```xml  
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
  
3.  <span data-ttu-id="0f669-112">Créez une instance <xref:System.ServiceModel.Description.WsdlImporter> (en passant l'instance <xref:System.ServiceModel.Description.MetadataSet> qui contient les documents WSDL à importer), puis appelez <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> :</span><span class="sxs-lookup"><span data-stu-id="0f669-112">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);          System.Collections.ObjectModel.Collection<ContractDescription> contracts  = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f669-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f669-113">See Also</span></span>  
 [<span data-ttu-id="0f669-114">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="0f669-114">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="0f669-115">Exportation et importation de métadonnées</span><span class="sxs-lookup"><span data-stu-id="0f669-115">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)  
 [<span data-ttu-id="0f669-116">Publication WSDL personnalisée</span><span class="sxs-lookup"><span data-stu-id="0f669-116">Custom WSDL Publication</span></span>](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
