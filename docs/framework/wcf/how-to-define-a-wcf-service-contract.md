---
title: "Comment : définir un contrat de service Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: "58"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 062167742a70307949624066b8607a37d5c7ed71
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Comment : définir un contrat de service Windows Communication Foundation
Il s'agit de la première des six tâches requises pour créer une application de base [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]. Pour une vue d’ensemble des six tâches, consultez la [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) rubrique.  
  
 Lors de la création d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], la première tâche consiste à définir un contrat de service. Le contrat de service spécifie les opérations prises en charge par le service. Une opération peut être considérée comme une méthode de service Web. Les contrats sont créés en définissant une interface C++, C# ou Visual Basic (VB). Chaque méthode dans l'interface correspond à une opération de service spécifique. Chaque interface doit avoir le <xref:System.ServiceModel.ServiceContractAttribute> qui s'applique à elle et chaque opération doit avoir l'attribut <xref:System.ServiceModel.OperationContractAttribute> qui s'applique à elle. Si une méthode dans une interface qui a l'attribut <xref:System.ServiceModel.ServiceContractAttribute> n'a pas l'attribut <xref:System.ServiceModel.OperationContractAttribute>, cette méthode n'est pas exposée par le service.  
  
 Le code utilisé pour cette tâche est fourni dans l'exemple qui suit la procédure.  
  
### <a name="to-define-a-service-contract"></a>Pour définir un contrat de service  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] en tant qu’administrateur en cliquant sur le programme dans le **Démarrer** menu et en sélectionnant **exécuter en tant qu’administrateur**.  
  
2.  Créez un projet bibliothèque du Service WCF en cliquant sur le **fichier** menu et en sélectionnant **nouveau**, **projet**. Dans le **nouveau projet** boîte de dialogue, sur le côté gauche de la boîte de dialogue développez **Visual C#** pour un projet c# ou **autres langages** , puis **Visual Basic** pour un projet Visual Basic. Sous la langue sélectionnée, sélectionnez **WCF** et une liste des modèles de projet s’affiche sur la section centrale de la boîte de dialogue. Sélectionnez **bibliothèque du Service WCF**et le type `GettingStartedLib` dans les **nom** zone de texte et `GettingStarted` dans les **nom de la Solution** zone de texte en bas de la boîte de dialogue.  
  
3.  Visual Studio crée le projet qui contient 3 fichiers : IService1.cs (ou IService1.vb), Service1.cs (ou Service1.vb) et App.config.  Le fichier IService1 contient un contrat de service par défaut.  Le fichier Service1 contient une implémentation par défaut du contrat de service. Le fichier App.config contient la configuration nécessaire pour charger le service par défaut avec l'hôte de service WCF Visual Studio. Pour plus d’informations sur l’outil de l’hôte de Service WCF, consultez [hôte de Service WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  Ouvrez le fichier IService1.cs ou IService1.vb et supprimez le code dans la déclaration d'espace de noms en laissant la déclaration d'espace de noms. Dans la déclaration d'espace de noms, définissez une nouvelle interface appelée `ICalculator` comme indiqué dans le code ci-dessous.  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
            public interface ICalculator  
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
    }  
    ```  
  
    ```  
    ‘IService.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
        Public Interface ICalculator  
  
            <OperationContract()> _  
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
        End Interface  
    End Namespace  
    ```  
  
     Ce contrat définit une calculatrice en ligne. Notez que l'interface `ICalculator`est marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>. Cet attribut définit un espace de noms qui est utilisé pour lever l'ambiguïté du nom de contrat. Chaque opération de calculatrice est marquée avec l'attribut <xref:System.ServiceModel.OperationContractAttribute>.  
  
    > [!NOTE]
    >  Lorsque vous utilisez des attributs pour annoter une interface, un membre ou une classe, vous pouvez supprimer la partie « Attribute » du nom d'attribut. Par conséquent, <xref:System.ServiceModel.ServiceContractAttribute> devient `[ServiceContract]` dans C#, ou `<ServiceContract>` dans Visual Basic.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Guide pratique pour implémenter un contrat de service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Prise en main](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [L’auto-hébergement](../../../docs/framework/wcf/samples/self-host.md)
