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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ffe53d3e44f86feadc292eccb1692bd58a0c056
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="c4b1e-102">Comment : définir un contrat de service Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c4b1e-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="c4b1e-103">Il s'agit de la première des six tâches requises pour créer une application de base [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4b1e-103">This is the first of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="c4b1e-104">Pour une vue d’ensemble des six tâches, consultez la [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="c4b1e-105">Lors de la création d'un service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], la première tâche consiste à définir un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-105">When creating a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service, the first task is to define a service contract.</span></span> <span data-ttu-id="c4b1e-106">Le contrat de service spécifie les opérations prises en charge par le service.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="c4b1e-107">Une opération peut être considérée comme une méthode de service Web.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="c4b1e-108">Les contrats sont créés en définissant une interface C++, C# ou Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="c4b1e-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="c4b1e-109">Chaque méthode dans l'interface correspond à une opération de service spécifique.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="c4b1e-110">Chaque interface doit avoir le <xref:System.ServiceModel.ServiceContractAttribute> qui s'applique à elle et chaque opération doit avoir l'attribut <xref:System.ServiceModel.OperationContractAttribute> qui s'applique à elle.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="c4b1e-111">Si une méthode dans une interface qui a l'attribut <xref:System.ServiceModel.ServiceContractAttribute> n'a pas l'attribut <xref:System.ServiceModel.OperationContractAttribute>, cette méthode n'est pas exposée par le service.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>  
  
 <span data-ttu-id="c4b1e-112">Le code utilisé pour cette tâche est fourni dans l'exemple qui suit la procédure.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-112">The code used for this task is provided in the example following the procedure.</span></span>  
  
### <a name="to-define-a-service-contract"></a><span data-ttu-id="c4b1e-113">Pour définir un contrat de service</span><span class="sxs-lookup"><span data-stu-id="c4b1e-113">To define a service contract</span></span>  
  
1.  <span data-ttu-id="c4b1e-114">Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] en tant qu’administrateur en cliquant sur le programme dans le **Démarrer** menu et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-114">Open  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] as an administrator by right-clicking the program in the **Start** menu and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="c4b1e-115">Créez un projet bibliothèque du Service WCF en cliquant sur le **fichier** menu et en sélectionnant **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-115">Create a WCF Service Library project by clicking the **File** menu and selecting **New**, **Project**.</span></span> <span data-ttu-id="c4b1e-116">Dans le **nouveau projet** boîte de dialogue, sur le côté gauche de la boîte de dialogue développez **Visual C#** pour un projet c# ou **autres langages** , puis **Visual Basic** pour un projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-116">In the **New Project** dialog, on the left-hand side of the dialog expand **Visual C#** for a C# project or **Other Languages** and then **Visual Basic** for a Visual Basic project.</span></span> <span data-ttu-id="c4b1e-117">Sous la langue sélectionnée, sélectionnez **WCF** et une liste des modèles de projet s’affiche sur la section centrale de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-117">Under the language selected select **WCF** and a list of project templates will be displayed on the center section of the dialog.</span></span> <span data-ttu-id="c4b1e-118">Sélectionnez **bibliothèque du Service WCF**et le type `GettingStartedLib` dans les **nom** zone de texte et `GettingStarted` dans les **nom de la Solution** zone de texte en bas de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-118">Select **WCF Service Library**, and type `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>  
  
3.  <span data-ttu-id="c4b1e-119">Visual Studio crée le projet qui contient 3 fichiers : IService1.cs (ou IService1.vb), Service1.cs (ou Service1.vb) et App.config.  Le fichier IService1 contient un contrat de service par défaut.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-119">Visual Studio will create the project which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config.  The IService1 file contains a default service contract.</span></span>  <span data-ttu-id="c4b1e-120">Le fichier Service1 contient une implémentation par défaut du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-120">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="c4b1e-121">Le fichier App.config contient la configuration nécessaire pour charger le service par défaut avec l'hôte de service WCF Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-121">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="c4b1e-122">Pour plus d’informations sur l’outil de l’hôte de Service WCF, consultez [hôte de Service WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="c4b1e-122">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>  
  
4.  <span data-ttu-id="c4b1e-123">Ouvrez le fichier IService1.cs ou IService1.vb et supprimez le code dans la déclaration d'espace de noms en laissant la déclaration d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-123">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration leaving the namespace declaration.</span></span> <span data-ttu-id="c4b1e-124">Dans la déclaration d'espace de noms, définissez une nouvelle interface appelée `ICalculator` comme indiqué dans le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-124">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>  
  
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
  
     <span data-ttu-id="c4b1e-125">Ce contrat définit une calculatrice en ligne.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-125">This contract defines an online calculator.</span></span> <span data-ttu-id="c4b1e-126">Notez que l'interface `ICalculator`est marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-126">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="c4b1e-127">Cet attribut définit un espace de noms qui est utilisé pour lever l'ambiguïté du nom de contrat.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-127">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="c4b1e-128">Chaque opération de calculatrice est marquée avec l'attribut <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-128">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4b1e-129">Lorsque vous utilisez des attributs pour annoter une interface, un membre ou une classe, vous pouvez supprimer la partie « Attribute » du nom d'attribut.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-129">When using attributes to annotate an interface, member, or class, you can drop the "Attribute" part from the attribute name.</span></span> <span data-ttu-id="c4b1e-130">Par conséquent, <xref:System.ServiceModel.ServiceContractAttribute> devient `[ServiceContract]` dans C#, ou `<ServiceContract>` dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c4b1e-130">So <xref:System.ServiceModel.ServiceContractAttribute> becomes `[ServiceContract]` in C#, or `<ServiceContract>` in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b1e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4b1e-131">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="c4b1e-132">Guide pratique pour implémenter un contrat de service</span><span class="sxs-lookup"><span data-stu-id="c4b1e-132">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="c4b1e-133">Prise en main</span><span class="sxs-lookup"><span data-stu-id="c4b1e-133">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="c4b1e-134">L’auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="c4b1e-134">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
