---
title: "Erreurs XmlSerializer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Erreurs XmlSerializer
L'exemple de contrat d'erreur <xref:System.Xml.Serialization.XmlSerializer> illustre comment transmettre les informations relatives à une erreur d'un service à un client à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.  Il est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). Quelques lignes de code sont ajoutées au service pour permettre la conversion d'une exception interne en erreur.  Le client tente d'effectuer une opération de division par zéro pour imposer la génération d'une erreur sur le service.  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le contrat de calculatrice a été modifié afin d'y inclure un <xref:System.ServiceModel.FaultContractAttribute>, tel qu'illustré dans l'exemple de code suivant.  En outre, <xref:System.ServiceModel.XmlSerializerFormatAttribute> est utilisé pour activer la sérialisation à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.  La propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> a la valeur `true` dans cet attribut, ce qui demande au sérialiseur d'utiliser <xref:System.Xml.Serialization.XmlSerializer> pour lire et écrire les erreurs.  
  
```  
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 Lorsque vous générez le code pour le proxy client, vous devez appliquer l'indicateur **\/UseSerializerForFaults** à [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## Voir aussi  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute>   
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>