---
title: Prise en charge POCO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c471a6726d8f7e621d666e014b2363c088e2b0e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="poco-support"></a>Prise en charge POCO
Cet exemple illustre la prise en charge de la sérialisation pour les types non marqués, c'est-à-dire les types auxquels aucun attribut de sérialisation n'a été appliqué. Ces types sont parfois appelés types POCO (Plain Old CLR Object). <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données pour tous les types non marqués publics qui possèdent un constructeur par défaut. Les contrats de données vous permettent de transférer des données structurées vers des services et à partir de ceux-ci. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les types non marqués, consultez [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), mais utilise des nombres complexes au lieu de types numériques primitifs. Il est similaire à la [contrat de données de base](../../../../docs/framework/wcf/samples/basic-data-contract.md) exemple, à ceci près que le <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> attributs ne sont pas utilisés.  
  
 Le client est une application de console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 La classe `ComplexNumber` est utilisée dans `ServiceContract`. Le type `ComplexNumber` ne comporte pas les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute>, comme indiqué dans l'exemple de code suivant. Par défaut, l'ensemble des propriétés et des champs publics sont sérialisés.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [Types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md)
