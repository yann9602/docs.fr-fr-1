---
title: Setting the Use and Style Properties
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f69ce60e6c9ab98ef773fa54b1c057d3c2b3b48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="160ce-102">Setting the Use and Style Properties</span><span class="sxs-lookup"><span data-stu-id="160ce-102">Setting the Use and Style Properties</span></span>
<span data-ttu-id="160ce-103">Cet exemple illustre comment utiliser les propriétés Use et Style des attributs <xref:System.ServiceModel.XmlSerializerFormatAttribute> et <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="160ce-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="160ce-104">Ces propriétés affectent la manière dont les messages sont mis en forme.</span><span class="sxs-lookup"><span data-stu-id="160ce-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="160ce-105">Par défaut, la propriété de style, en fonction de laquelle le corps des messages est mis en forme, a pour valeur <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="160ce-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="160ce-106">Ces paramètres peuvent être spécifiés dans les contrats de service ou d'opération.</span><span class="sxs-lookup"><span data-stu-id="160ce-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="160ce-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="160ce-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="160ce-108">La propriété de style <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> détermine la manière dont les métadonnées WSDL du service sont mises en forme.</span><span class="sxs-lookup"><span data-stu-id="160ce-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="160ce-109">Cette propriété peut avoir les valeurs suivantes : <xref:System.ServiceModel.OperationFormatStyle.Document> et <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="160ce-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="160ce-110">RPC signifie que la représentation WSDL des messages échangés pour une opération contient des paramètres propres à un appel de procédure distante.</span><span class="sxs-lookup"><span data-stu-id="160ce-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="160ce-111">Voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="160ce-111">The following is an example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="160ce-112">Avec le style <xref:System.ServiceModel.OperationFormatStyle.Document>, la représentation WSDL contient un élément unique qui représente le document échangé pour une opération, tel qu'illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="160ce-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="160ce-113">La propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> détermine la mise en forme des messages.</span><span class="sxs-lookup"><span data-stu-id="160ce-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="160ce-114">Les valeurs possibles de cette propriété sont <xref:System.ServiceModel.OperationFormatUse.Literal> et <xref:System.ServiceModel.OperationFormatUse.Encoded>. Sa valeur par défaut est <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="160ce-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="160ce-115">Cette dernière valeur signifie que le message correspond à une instance littérale du schéma dans le WSDL, tel qu'illustré dans l'exemple document/littéral suivant.</span><span class="sxs-lookup"><span data-stu-id="160ce-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 <span data-ttu-id="160ce-116">Encoded signifie que les schémas en WSDL sont des spécifications abstraites encodées selon les règles trouvées dans SOAP 1.1, section 5.</span><span class="sxs-lookup"><span data-stu-id="160ce-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="160ce-117">Voici un exemple de document RPC/Encoded.</span><span class="sxs-lookup"><span data-stu-id="160ce-117">The following is an RPC/Encoded example.</span></span>  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 <span data-ttu-id="160ce-118">Le profil WS-I Basic Profile 1.0 ne permet pas d'utiliser <xref:System.ServiceModel.OperationFormatUse.Encoded>. Vous devez uniquement utiliser ce profil lorsque requis par les services hérités.</span><span class="sxs-lookup"><span data-stu-id="160ce-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="160ce-119">Le format de message `Encoded` est disponible uniquement lorsque le sérialiseur XmlSerializer est utilisé.</span><span class="sxs-lookup"><span data-stu-id="160ce-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>  
  
 <span data-ttu-id="160ce-120">Pour vous permettre de voir les messages envoyés et reçus, cet exemple est basé sur le [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="160ce-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span> <span data-ttu-id="160ce-121">La configuration du service et le code source ont été modifiés pour activer le suivi et l'enregistrement des messages et permettre leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="160ce-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="160ce-122">En outre, le <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> a été configurée sans sécurité, donc les messages enregistrés peuvent être affichées dans un format non chiffré.</span><span class="sxs-lookup"><span data-stu-id="160ce-122">In addition, the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="160ce-123">Les journaux de suivi qui en résulte (System.ServiceModel.e2e et Message.log) doivent être affichés à l’aide de la [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="160ce-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="160ce-124">Les suivis sont configurés de sorte à être créés dans le dossier C:\LOGS.</span><span class="sxs-lookup"><span data-stu-id="160ce-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="160ce-125">Créez ce dossier avant d’exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="160ce-125">Create the folder before running the sample.</span></span> <span data-ttu-id="160ce-126">Pour afficher le contenu du message dans l’outil Trace Viewer, sélectionnez **Messages** de gauche et les volets de droite de l’outil.</span><span class="sxs-lookup"><span data-stu-id="160ce-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>  
  
 <span data-ttu-id="160ce-127">Dans le contrat de service défini par le code suivant, la propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a la valeur <xref:System.ServiceModel.OperationFormatUse> et le format du corps du message au lieu d'avoir la valeur par défaut <xref:System.ServiceModel.OperationFormatStyle> a la valeur <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="160ce-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
XmlSerializerFormat(Style = OperationFormatStyle.Rpc,   
                                 Use = OperationFormatUse.Encoded)]  
public interface IUseAndStyleCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="160ce-128">Pour se rendre compte des différences existant entre les paramètres <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> et <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A>, modifiez-les au niveau du service, régénérez le client, exécutez l'exemple, puis examinez le fichier c:\logs\message.logs à l'aide de l'outil Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="160ce-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="160ce-129">Observez également leur impact sur les métadonnées en consultant http://localhost/ServiceModelSamples/service.svc? wsdl.</span><span class="sxs-lookup"><span data-stu-id="160ce-129">Also observe the impact on the metadata by viewing http://localhost/ServiceModelSamples/service.svc?wsdl.</span></span> <span data-ttu-id="160ce-130">En principe, les métadonnées des services sont réparties sur plusieurs pages.</span><span class="sxs-lookup"><span data-stu-id="160ce-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="160ce-131">La page wsdl principale contient les liaisons WSDL, mais ouvrez le fichier http://localhost/ServiceModelSamples/service.svc? wsdl=wsdl0 afin d'observer les définitions de message.</span><span class="sxs-lookup"><span data-stu-id="160ce-131">The main wsdl page contains the WSDL bindings, but view http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 to observe the message definitions.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="160ce-132">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="160ce-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="160ce-133">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="160ce-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="160ce-134">Créez un répertoire C:\LOGS pour l'enregistrement des messages.</span><span class="sxs-lookup"><span data-stu-id="160ce-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="160ce-135">Accordez à l'utilisateur des droits d'accès en écriture au service réseau pour ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="160ce-135">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="160ce-136">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="160ce-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="160ce-137">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="160ce-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="160ce-138">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="160ce-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="160ce-139">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="160ce-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="160ce-140">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="160ce-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="160ce-141">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="160ce-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a><span data-ttu-id="160ce-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="160ce-142">See Also</span></span>
