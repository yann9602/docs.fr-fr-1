---
title: "Développement de pipeline"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ad577145c26b9c43e8b7fb3b61f27f374ff9298
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="pipeline-development"></a>Développement de pipeline
Le pipeline de complément est le chemin d’accès des segments de pipeline que l’application hôte et son complément doivent utiliser pour communiquer entre eux.  
  
 L’illustration suivante montre le pipeline de communication et ses segments.  
  
 ![Ajouter &#45; dans le modèle de pipeline. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Pipeline de complément  
  
 L’application hôte est à une extrémité du pipeline et le complément est à l’autre extrémité. À partir de chaque extrémité et le déplacement vers le milieu, l’application hôte et le complément ont une classe de base abstraite qui définit une vue du modèle d’objet qu’ils partagent. Ces types (classes) constituent le segment de pipeline de complément, la vue et la vue hôte du segment de pipeline de complément. Le segment de pipeline de complément, la vue contient souvent plus d’une classe abstraite, mais la classe héritant de la macro complémentaire est connue en tant que la base de complément.  
  
 Le segment de pipeline adaptateur côté complément et la conversion de segment de pipeline adaptateur côté hôte le flux de types entre leurs segments de pipeline de vue et le segment de pipeline du contrat. Le segment central du pipeline est un contrat qui est dérivé de la <xref:System.AddIn.Contract.IContract> interface. Ce contrat définit les méthodes que l’application hôte et son complément utiliseront.  
  
 Si vous chargez l’hôte et le complément dans des domaines d’application distincts, vous avez une limite d’isolation qui sépare la portée de l’application hôte à partir de l’étendue de la macro complémentaire. Le contrat est le seul assembly est chargé dans l’hôte et les domaines d’application du complément. L’ordinateur hôte et le complément chaque font référence uniquement à leur vue des méthodes de contrat. Par conséquent, ils sont séparés par une couche d’abstraction du contrat.  
  
 Pour développer des segments de pipeline, vous devez créer une structure de répertoires qui les contiennent. Pour plus d’informations sur les spécifications de développement et les indications de portée, consultez [les exigences de développement de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 L’illustration suivante montre les types qui composent les segments de pipeline. Les noms des types indiqués dans l’illustration sont arbitraires, mais tous les types à l’exception de l’hôte et l’ordinateur hôte permet d’afficher les attributs du complément, requièrent afin qu’ils puissent être détectés par les méthodes qui génèrent une banque d’informations.  
  
 ![Ajouter &#45; dans le modèle avec des attributs requis sur les types. ] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Pipeline de complément avec types  
  
 Le tableau suivant décrit les segments de pipeline pour l’activation d’un complément. Pour plus d’informations sur ces segments, consultez [contrats, les vues et les adaptateurs](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Segment de pipeline|Description|  
|----------------------|-----------------|  
|Hôte|L’assembly d’application qui crée une instance d’un complément.|  
|Vue hôte du complément|Représente l’affichage de l’application hôte des types d’objets et méthodes utilisés pour communiquer avec le complément. La vue hôte est une interface ou une classe de base abstraite.|  
|Adaptateur côté hôte|Un assembly avec une ou plusieurs classes qui adapte des méthodes vers et depuis le contrat.<br /><br /> Ce segment de pipeline est identifié à l’aide de la <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribut.<br /><br /> Les assemblys composés de plusieurs modules ne sont pas pris en charge.|  
|Contrat|Une interface qui est dérivée de la <xref:System.AddIn.Contract.IContract> interface et qui définit le protocole pour communiquer des types entre l’hôte et son complément.<br /><br /> Ce segment de pipeline est identifié en définissant le <xref:System.AddIn.Pipeline.AddInContractAttribute> attribut.|  
|Adaptateur côté complément|Un assembly avec une ou plusieurs classes qui adapte des méthodes vers et depuis le contrat.<br /><br /> Ce segment de pipeline est identifié à l’aide de la <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribut.<br /><br /> Chaque assembly dans le répertoire de l’adaptateur côté complément qui contient un type qui a un <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribut est chargé dans domaine d’application du complément.<br /><br /> Chaque assembly dans le répertoire côté complément est chargé dans son propre domaine d’application.<br /><br /> Les assemblys composés de plusieurs modules ne sont pas pris en charge.|  
|Vue complément|Un assembly qui représente la vue du complément des types d’objets et les méthodes utilisées pour communiquer avec l’hôte. La vue du complément est une interface ou une classe de base abstraite.<br /><br /> Ce segment de pipeline est identifié à l’aide de la <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribut.<br /><br /> Chaque assembly du répertoire AddInViews qui contient un type qui a un <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribut est chargé dans domaine d’application du complément.|  
|Complément|Un type instancié qui exécute un service pour l’ordinateur hôte.|  
  
## <a name="pipeline-activation-path"></a>Chemin d’Activation du pipeline  
 L’illustration suivante montre l’activation de types lorsqu’un complément est activé. Il montre également le passage d’objets à l’hôte, telles que les résultats d’un calcul ou une collection d’objets. Il s’agit du scénario le plus courant.  
  
 ![Ajouter &#45; dans le modèle avec le chemin d’accès d’activation. ] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Chemin d’activation du complément à l’hôte  
  
 Le chemin d’accès de l’activation du pipeline se présente comme suit :  
  
1.  L’application hôte Active le complément avec le <xref:System.AddIn.Hosting.AddInToken.Activate%2A> (méthode).  
  
2.  La vue du complément, complément, adaptateur côté complément et les assemblys de contrat sont chargés dans domaine d’application du complément.  
  
3.  Une instance de l’adaptateur côté complément est créée à l’aide de la vue de complément (avec la classe identifiée par le <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribut) en tant que son constructeur. L’adaptateur côté complément hérite du contrat.  
  
4.  L’adaptateur côté complément, qui est typée en tant que le contrat, est passé au constructeur de l’adaptateur côté hôte au-delà des limites d’isolement (facultatif).  
  
5.  La vue de l’hôte de l’adaptateur de complément, côté hôte et les assemblys de contrat sont chargés dans le domaine d’application de l’hôte.  
  
6.  Une instance de l’adaptateur côté hôte est créée à l’aide du contrat comme son constructeur. L’adaptateur côté hôte hérite de la vue hôte du complément.  
  
7.  L’hôte possède le complément, ce qui est de type comme afficher de l’ajout de l’hôte et peut continuer à appeler ses méthodes.  
  
## <a name="walkthroughs"></a>Procédures pas à pas  
 Il existe trois rubriques de procédure pas à pas qui décrivent comment créer des pipelines à l’aide de Visual Studio :  
  
-   [Procédure pas à pas : création d’une application extensible](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Décrit un complément calculatrice qui effectue l’addition, soustraction, multiplication et calculs de division pour l’hôte.  
  
-   [Procédure pas à pas : L’activation de la compatibilité descendante lorsque votre hôte change](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Décrit un complément de calculatrice avec des fonctions de calcul améliorées et comment assurer la compatibilité avec le premier calcul complément.  
  
-   [Procédure pas à pas : Passage de Collections entre les hôtes et les compléments](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Explique comment passer des collections de données sur le pipeline à l’aide d’un scénario de librairie.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios de Pipeline de complément](http://msdn.microsoft.com/en-us/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [Compléments et extensibilité](../../../docs/framework/add-ins/index.md)
