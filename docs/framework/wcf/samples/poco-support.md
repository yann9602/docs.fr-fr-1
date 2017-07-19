---
title: "Prise en charge POCO | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Prise en charge POCO
Cet exemple illustre la prise en charge de la sérialisation pour les types non marqués, c'est\-à\-dire les types auxquels aucun attribut de sérialisation n'a été appliqué. Ces types sont parfois appelés types POCO \(Plain Old CLR Object\).<xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données pour tous les types non marqués publics qui possèdent un constructeur par défaut.Les contrats de données vous permettent de transférer des données structurées vers des services et à partir de ceux\-ci.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les types non marqués, consultez [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Cet exemple est basé sur l'exemple de mise en route \(voir [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md)\), mais utilise des nombres complexes au lieu de types numériques primitifs.Il est également semblable à l'exemple [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md), mais les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> ne sont pas utilisés.  
  
 Le client est une application de console \(.exe\) et le service est hébergé par les services IIS \(Internet Information Services\).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent en fin de rubrique.  
  
 La classe `ComplexNumber` est utilisée dans `ServiceContract`.Le type `ComplexNumber` ne comporte pas les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute>, comme indiqué dans l'exemple de code suivant.Par défaut, l'ensemble des propriétés et des champs publics sont sérialisés.  
  
```  
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure figurant dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## Voir aussi  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>   
 [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md)