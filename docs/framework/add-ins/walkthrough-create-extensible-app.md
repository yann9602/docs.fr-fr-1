---
title: "Procédure pas à pas : création d'une application extensible"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6609f30844421f94965fbe05114db96ed8edbb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-an-extensible-application"></a>Procédure pas à pas : création d'une application extensible
Cette procédure pas à pas explique comment créer un pipeline pour un complément qui exécute des fonctions de calculatrice simple. Il ne présente pas un scénario réel ; au lieu de cela, il illustre les fonctionnalités de base d’un pipeline et la manière dont un complément peut fournir des services pour un ordinateur hôte.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une solution Visual Studio.  
  
-   Création de la structure de répertoires du pipeline.  
  
-   Création du contrat et des vues.  
  
-   Création de l’adaptateur côté complément.  
  
-   Création de l’adaptateur côté hôte.  
  
-   Création de l’hôte.  
  
-   Création de la macro complémentaire.  
  
-   Déploiement du pipeline.  
  
-   L’application hôte en cours d’exécution.  
  
 Ce pipeline passe uniquement des types sérialisables (<xref:System.Double> et <xref:System.String>), entre l’hôte et le complément. Pour obtenir un exemple qui montre comment passer des collections de types de données complexes, consultez [procédure pas à pas : passage de Collections entre les hôtes et les compléments](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 Le contrat pour ce pipeline définit un modèle d’objet de quatre opérations arithmétiques : ajouter, de soustraire, de multiplier et de diviser. L’hôte fournit le complément une équation à calculer, par exemple 2 + 2, et le complément retourne le résultat à l’hôte.  
  
 La version 2 de la calculatrice de complément fournit des possibilités de calcul plus et montre comment le contrôle de version. Il est décrit dans [procédure pas à pas : l’activation de la compatibilité descendante en tant que vos modifications de l’hôte](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les éléments suivants sont nécessaires pour effectuer cette procédure pas à pas :  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="creating-a-visual-studio-solution"></a>Création d’une Solution Visual Studio  
 Utilisez une solution dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour contenir les projets de vos segments de pipeline.  
  
#### <a name="to-create-the-pipeline-solution"></a>Pour créer la solution de pipeline  
  
1.  Dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], créez un nouveau projet nommé `Calc1Contract`. Baser sur le **bibliothèque de classes** modèle.  
  
2.  Nommez la solution `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>Création de la Structure de répertoires du Pipeline  
 Le modèle de complément requiert les assemblys du segment de pipeline à placer dans une structure de répertoire spécifié. Pour plus d’informations sur la structure du pipeline, consultez [les exigences de développement de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>Pour créer la structure de répertoires du pipeline  
  
1.  Créer un dossier d’application de n’importe où sur votre ordinateur.  
  
2.  Dans ce dossier, créez la structure suivante :  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     Il n’est pas nécessaire de placer la structure de dossiers de pipeline dans votre dossier d’application ; Il est fait ici uniquement pour des raisons pratiques. À l’étape appropriée, la procédure pas à pas explique comment modifier le code si la structure de dossiers de pipeline est dans un autre emplacement. Consultez la discussion active des spécifications du pipeline dans [les exigences de développement de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  Le `CalcV2` dossier n’est pas utilisé dans cette procédure pas à pas ; il s’agit d’un espace réservé pour [procédure pas à pas : l’activation de la compatibilité descendante en tant que vos modifications de l’hôte](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Création du contrat et les vues  
 Le segment de contrat pour ce pipeline définit la `ICalc1Contract` interface qui définit les quatre méthodes : `add`, `subtract`, `multiply`, et `divide`.  
  
#### <a name="to-create-the-contract"></a>Pour créer le contrat  
  
1.  Dans la solution Visual Studio nommée `CalculatorV1`, ouvrez le `Calc1Contract` projet.  
  
2.  Dans **l’Explorateur de solutions**, ajoutez des références aux assemblys suivants à la `Calc1Contract` projet :  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  Dans **l’Explorateur de solutions**, excluez la classe par défaut qui est ajoutée au nouveau **bibliothèque de classes** projets.  
  
4.  Dans **l’Explorateur de solutions**, ajouter un nouvel élément au projet, à l’aide de la **Interface** modèle. Dans le **ajouter un nouvel élément** boîte de dialogue, nom de l’interface `ICalc1Contract`.  
  
5.  Dans le fichier d’interface, ajoutez des références d’espace de noms aux <xref:System.AddIn.Contract> et <xref:System.AddIn.Pipeline>.  
  
6.  Utilisez le code suivant pour terminer ce segment de contrat. Notez que cette interface doit avoir le <xref:System.AddIn.Pipeline.AddInContractAttribute> attribut.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  Si vous le souhaitez, générez la solution Visual Studio. La solution ne peut pas être exécutée jusqu'à ce que la dernière procédure, mais la générer après que chaque procédure garantit que chaque projet est corriger.  
  
 Étant donné que la vue du complément et l’hôte de vue de la macro complémentaire ont généralement le même code, en particulier dans la première version d’un complément, vous pouvez facilement créer ces vues en même temps. Ils diffèrent par un seul facteur : la vue de complément requiert le <xref:System.AddIn.Pipeline.AddInBaseAttribute> d’attributs, tandis que la vue hôte du complément ne nécessite pas tous les attributs.  
  
#### <a name="to-create-the-add-in-view"></a>Pour créer la vue de complément  
  
1.  Ajoutez un nouveau projet nommé `Calc1AddInView` à la `CalculatorV1` solution. Baser sur le **bibliothèque de classes** modèle.  
  
2.  Dans **l’Explorateur de solutions**, ajoutez une référence à System.AddIn.dll à la `Calc1AddInView` projet.  
  
3.  Dans **l’Explorateur de solutions**, excluez la classe par défaut qui est ajoutée au nouveau **bibliothèque de classes** des projets et ajouter un nouvel élément au projet, à l’aide de la **Interface** modèle. Dans le **ajouter un nouvel élément** boîte de dialogue, nom de l’interface `ICalculator`.  
  
4.  Dans le fichier d’interface, ajoutez une référence d’espace de noms à <xref:System.AddIn.Pipeline>.  
  
5.  Utilisez le code suivant pour terminer cette vue de complément. Notez que cette interface doit avoir le <xref:System.AddIn.Pipeline.AddInBaseAttribute> attribut.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  Si vous le souhaitez, générez la solution Visual Studio.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Pour créer la vue hôte du complément  
  
1.  Ajoutez un nouveau projet nommé `Calc1HVA` à la `CalculatorV1` solution. Baser sur le **bibliothèque de classes** modèle.  
  
2.  Dans **l’Explorateur de solutions**, excluez la classe par défaut qui est ajoutée au nouveau **bibliothèque de classes** des projets et ajouter un nouvel élément au projet, à l’aide de la **Interface** modèle. Dans le **ajouter un nouvel élément** boîte de dialogue, nom de l’interface `ICalculator`.  
  
3.  Dans le fichier d’interface, utilisez le code suivant pour terminer la vue hôte du complément.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  Si vous le souhaitez, générez la solution Visual Studio.  
  
## <a name="creating-the-add-in-side-adapter"></a>Création de l’adaptateur côté complément  
 Cet adaptateur côté complément se compose d’une carte de vue en contrat. Ce segment de pipeline convertit les types à partir de la vue du complément pour le contrat.  
  
 Dans ce pipeline, le complément fournit un service à l’hôte, et les types de flux à partir du complément à l’hôte. Car aucun type de flux de l’hôte vers le complément, vous n’avez pas à inclure un adaptateur de contrat en vue du côté complément de ce pipeline.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Pour créer l’adaptateur côté complément  
  
1.  Ajoutez un nouveau projet nommé `Calc1AddInSideAdapter` à la `CalculatorV1` solution. Baser sur le **bibliothèque de classes** modèle.  
  
2.  Dans **l’Explorateur de solutions**, ajoutez des références aux assemblys suivants à la `Calc1AddInSideAdapter` projet :  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Ajoutez des références de projet pour les projets pour les segments de pipeline adjacents :  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Sélectionnez chaque référence de projet et dans **propriétés** définir **copie locale** à **False**. En Visual Basic, utilisez la **références** onglet de **propriétés du projet** définir **copie locale** à **False** pour les deux références de projet.  
  
5.  Renommez la classe du projet par défaut `CalculatorViewToContractAddInSideAdapter`.  
  
6.  Dans le fichier de classe, ajoutez des références d’espace de noms aux <xref:System.AddIn.Pipeline>.  
  
7.  Dans le fichier de classe, ajoutez des références d’espace de noms pour les segments adjacents : `CalcAddInViews` et `CalculatorContracts`. (En Visual Basic, ces références d’espace de noms sont `Calc1AddInView.CalcAddInViews` et `Calc1Contract.CalculatorContracts`, sauf si vous avez désactivé les espaces de noms par défaut dans vos projets Visual Basic.)  
  
8.  Appliquer le <xref:System.AddIn.Pipeline.AddInAdapterAttribute> attribut le `CalculatorViewToContractAddInSideAdapter` (classe), pour l’identifier comme l’adaptateur côté complément.  
  
9. Rendre le `CalculatorViewToContractAddInSideAdapter` héritent de la classe <xref:System.AddIn.Pipeline.ContractBase>, qui fournit une implémentation par défaut de la <xref:System.AddIn.Contract.IContract> de l’interface et implémenter l’interface de contrat pour le pipeline, `ICalc1Contract`.  
  
10. Ajoutez un constructeur public qui accepte un `ICalculator`, il met en cache dans un champ privé et appelle le constructeur de classe de base.  
  
11. Pour implémenter les membres de `ICalc1Contract`, appelez simplement les membres correspondants de le `ICalculator` instance qui est passée au constructeur et retourne les résultats. Cela s’adapte à la vue (`ICalculator`) au contrat (`ICalc1Contract`).  
  
     Le code suivant montre l’adaptateur côté complément terminé.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. Si vous le souhaitez, générez la solution Visual Studio.  
  
## <a name="creating-the-host-side-adapter"></a>Création de l’adaptateur côté hôte  
 Cet adaptateur côté hôte se compose d’un adaptateur de contrat en vue. Ce segment adapte le contrat à la vue hôte du complément.  
  
 Dans ce pipeline, le complément fournit un service à l’hôte et le flux de types à partir de la macro complémentaire pour l’ordinateur hôte. Car aucun type de flux de l’hôte vers le complément, il est inutile d’inclure une carte de vue en contrat.  
  
 Pour implémenter la gestion de la durée de vie, utilisez un <xref:System.AddIn.Pipeline.ContractHandle> objet à attacher un jeton de durée de vie pour le contrat. Vous devez conserver une référence à ce handle dans l’ordre pour la gestion de durée de vie. Une fois que le jeton est appliqué, aucune programmation supplémentaire n’est requise, car le système de complément peut supprimer les objets lorsqu’ils ne sont plus utilisés et les rendre disponibles pour le garbage collection. Pour plus d'informations, consultez [Gestion de la durée de vie](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Pour créer l’adaptateur côté hôte  
  
1.  Ajoutez un nouveau projet nommé `Calc1HostSideAdapter` à la `CalculatorV1` solution. Baser sur le **bibliothèque de classes** modèle.  
  
2.  Dans **l’Explorateur de solutions**, ajoutez des références aux assemblys suivants à la `Calc1HostSideAdapter` projet :  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Ajoutez des références de projet pour les projets pour les segments adjacents :  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Sélectionnez chaque référence de projet et dans **propriétés** définir **copie locale** à **False**. En Visual Basic, utilisez la **références** onglet de **propriétés du projet** définir **copie locale** à **False** pour les deux références de projet.  
  
5.  Renommez la classe du projet par défaut `CalculatorContractToViewHostSideAdapter`.  
  
6.  Dans le fichier de classe, ajoutez des références d’espace de noms aux <xref:System.AddIn.Pipeline>.  
  
7.  Dans le fichier de classe, ajoutez des références d’espace de noms pour les segments adjacents : `CalcHVAs` et `CalculatorContracts`. (En Visual Basic, ces références d’espace de noms sont `Calc1HVA.CalcHVAs` et `Calc1Contract.CalculatorContracts`, sauf si vous avez désactivé les espaces de noms par défaut dans vos projets Visual Basic.)  
  
8.  Appliquer le <xref:System.AddIn.Pipeline.HostAdapterAttribute> attribut le `CalculatorContractToViewHostSideAdapter` (classe), pour l’identifier comme le segment d’adaptateur côté hôte.  
  
9. Rendre le `CalculatorContractToViewHostSideAdapter` classe implémente l’interface qui représente la vue hôte du complément : `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` en Visual Basic).  
  
10. Ajoutez un constructeur public qui accepte le type de contrat de pipeline, `ICalc1Contract`. Le constructeur doit mettre en cache la référence au contrat. Il doit également créer et mettre en cache un nouveau <xref:System.AddIn.Pipeline.ContractHandle> pour le contrat, pour gérer la durée de vie de la macro complémentaire.  
  
    > [!IMPORTANT]
    >  Le <xref:System.AddIn.Pipeline.ContractHandle> est essentiel à la gestion de la durée de vie. Si vous ne pouvez pas conserver une référence à la <xref:System.AddIn.Pipeline.ContractHandle> de l’objet, le garbage collection récupère et le pipeline arrêtera lorsque votre programme n’attend pas cela. Cela peut entraîner des erreurs qui sont difficiles à diagnostiquer, telles que <xref:System.AppDomainUnloadedException>. Arrêt étant une phase normale de la durée de vie d’un pipeline, il n’existe aucun moyen pour le code de gestion de durée de vie détecter que cette condition est une erreur.  
  
11. Pour implémenter les membres de `ICalculator`, appelez simplement les membres correspondants de le `ICalc1Contract` instance qui est passée au constructeur et retourne les résultats. Cela adapte le contrat (`ICalc1Contract`) à la vue (`ICalculator`).  
  
     Le code suivant montre l’adaptateur côté hôte terminé.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. Si vous le souhaitez, générez la solution Visual Studio.  
  
## <a name="creating-the-host"></a>Création de l’hôte  
 Une application hôte interagit avec le complément via la vue hôte du complément. Il utilise des méthodes d’activation et de découverte de complément fournies par le <xref:System.AddIn.Hosting.AddInStore> et <xref:System.AddIn.Hosting.AddInToken> classes pour effectuer les opérations suivantes :  
  
-   Mettre à jour le cache des informations de pipeline et de complément.  
  
-   Rechercher des compléments de type de vue hôte, `ICalculator`, sous le répertoire racine du pipeline spécifié.  
  
-   Invite l’utilisateur de spécifier le complément à utiliser.  
  
-   Activer le complément sélectionné dans un nouveau domaine d’application avec un niveau de confiance de sécurité spécifié.  
  
-   Exécutez personnalisé `RunCalculator` méthode qui appelle les méthodes du complément comme spécifié par la vue hôte du complément.  
  
#### <a name="to-create-the-host"></a>Pour créer l’hôte  
  
1.  Ajoutez un nouveau projet nommé `Calc1Host` à la `CalculatorV1` solution. Baser sur le **Application Console** modèle.  
  
2.  Dans **l’Explorateur de solutions**, ajoutez une référence à l’assembly System.AddIn.dll à la `Calc1Host` projet.  
  
3.  Ajouter une référence de projet à la `Calc1HVA` projet. Sélectionnez la référence de projet et dans **propriétés** définir **copie locale** à **False**. En Visual Basic, utilisez la **références** onglet de **propriétés du projet** définir **copie locale** à **False**.  
  
4.  Renommez le fichier de classe (module en Visual Basic) `MathHost1`.  
  
5.  En Visual Basic, utilisez la **Application** onglet de la **propriétés du projet** boîte de dialogue pour définir **objet de démarrage** à **Sub Main**.  
  
6.  Dans le fichier de classe ou module, ajoutez une référence d’espace de noms à <xref:System.AddIn.Hosting>.  
  
7.  Dans le fichier de classe ou module, ajoutez une référence d’espace de noms pour la vue hôte du complément : `CalcHVAs`. (En Visual Basic, cette référence d’espace de noms est `Calc1HVA.CalcHVAs`, sauf si vous avez désactivé les espaces de noms par défaut dans vos projets Visual Basic.)  
  
8.  Dans **l’Explorateur de solutions**, sélectionnez la solution et à partir de la **projet** menu Choisissez **propriétés**. Dans le **les Pages de propriétés de Solution** boîte de dialogue, définissez la **projet de démarrage unique** à ce projet d’application hôte.  
  
9. Dans le fichier de classe ou module, utilisez le <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> pour mettre à jour le cache. Utilisez le <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> méthode pour obtenir une collection de jetons et le <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> méthode permettant d’activer un complément.  
  
     Le code suivant montre l’application hôte terminée.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Ce code suppose que la structure de dossiers du pipeline se trouve dans le dossier d’application. Si vous avez localisé ailleurs, modifiez la ligne de code qui définit le `addInRoot` variable, afin que la variable contient le chemin d’accès à votre structure de répertoires du pipeline.  
  
     Le code utilise un `ChooseCalculator` méthode pour répertorier les jetons et inviter l’utilisateur à choisir un complément. Le `RunCalculator` méthode invite l’utilisateur pour les expressions mathématiques simples, analyse les expressions à l’aide de la `Parser` classe et affiche les résultats retournés par le complément.  
  
10. Si vous le souhaitez, générez la solution Visual Studio.  
  
## <a name="creating-the-add-in"></a>Création du complément  
 Un complément implémente les méthodes spécifiées par la vue de complément. Ce complément implémente la `Add`, `Subtract`, `Multiply`, et `Divide` opérations et renvoie les résultats à l’hôte.  
  
#### <a name="to-create-the-add-in"></a>Pour créer le complément  
  
1.  Ajoutez un nouveau projet nommé `AddInCalcV1` à la `CalculatorV1` solution. Baser sur le **bibliothèque de classes** modèle.  
  
2.  Dans **l’Explorateur de solutions**, ajoutez une référence à l’assembly System.AddIn.dll au projet.  
  
3.  Ajouter une référence de projet à la `Calc1AddInView` projet. Sélectionnez la référence de projet et dans **propriétés**, définissez **copie locale** à **False**. En Visual Basic, utilisez la **références** onglet de **propriétés du projet** définir **copie locale** à **False** pour la référence de projet.  
  
4.  Nom de la classe `AddInCalcV1`.  
  
5.  Dans le fichier de classe, ajoutez une référence d’espace de noms à <xref:System.AddIn> et le segment de vue de complément : `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` en Visual Basic).  
  
6.  Appliquer le <xref:System.AddIn.AddInAttribute> attribut le `AddInCalcV1` (classe), pour identifier la classe comme un complément.  
  
7.  Rendre le `AddInCalcV1` classe implémente l’interface qui représente la vue de complément : `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` en Visual Basic).  
  
8.  Implémenter les membres de `ICalculator` en retournant les résultats des calculs appropriés.  
  
     Le code suivant montre le complément terminé.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. Si vous le souhaitez, générez la solution Visual Studio.  
  
## <a name="deploying-the-pipeline"></a>Déploiement du Pipeline  
 Vous êtes maintenant prêt à générer et déployer les segments de complément à la structure de répertoires du pipeline requise.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>Pour déployer les segments vers le pipeline  
  
1.  Pour chaque projet dans la solution, utilisez la **générer** onglet de **propriétés du projet** (le **compiler** onglet dans Visual Basic) pour définir la valeur de la **chemin de sortie**  (le **chemin de sortie de génération** en Visual Basic). Si vous avez nommé votre dossier d’application `MyApp`, par exemple, vos projets seraient générés dans les dossiers suivants :  
  
    |Projet|Chemin d'accès|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|MyApp|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|MyApp|  
  
    > [!NOTE]
    >  Si vous avez décidé de placer votre structure de dossiers de pipeline dans un emplacement autre que votre dossier d’application, vous devez modifier les chemins d’accès indiqués dans le tableau en conséquence. Consultez la discussion active des spécifications du pipeline dans [les exigences de développement de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Générez la solution Visual Studio.  
  
3.  Vérifiez les répertoires d’application et du pipeline pour vous assurer que les assemblys ont été copiés vers les répertoires appropriés et qu’aucune copie supplémentaire des assemblys ont été installés dans des dossiers incorrects.  
  
    > [!NOTE]
    >  Si vous n’avez pas modifié **copie locale** à **False** pour le `Calc1AddInView` projet référence dans le `AddInCalcV1` projet, des problèmes de contexte de chargeur empêche le complément qui est situé.  
  
     Pour plus d’informations sur le déploiement vers le pipeline, consultez [les exigences de développement de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Exécution de l’Application hôte  
 Vous êtes maintenant prêt à exécuter l’hôte et d’interagir avec le complément.  
  
#### <a name="to-run-the-host-application"></a>Pour exécuter l’application hôte  
  
1.  À l’invite de commandes, accédez au répertoire de l’application et exécutez l’application hôte, `Calc1Host.exe`.  
  
2.  L’hôte recherche tous les compléments disponibles de son type et vous invite à sélectionner un complément. Entrez **1** pour le complément disponible uniquement.  
  
3.  Entrez une équation pour le calcul, tel que **2 + 2**. Il doit exister des espaces entre les nombres et l’opérateur.  
  
4.  Type **quitter** et appuyez sur la **entrée** touche pour fermer l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : L’activation de la compatibilité descendante lorsque votre hôte change](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [Procédure pas à pas : Passage de Collections entre les hôtes et les compléments](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [Exigences de développement de pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [Contrats, les vues et les adaptateurs](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md)
