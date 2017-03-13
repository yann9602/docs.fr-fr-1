---
title: "Extending the My Namespace in Visual Basic | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AddingMyExtensions"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
  - "My namespace, extending"
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Extending the My Namespace in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

L'espace de noms `My` de Visual Basic expose des propriétés et des méthodes qui vous permettent de tirer facilement parti de la puissance du .NET Framework.  Cet espace de noms permet de corriger les problèmes de programmation courants en réduisant la plupart du temps une tâche complexe à une simple ligne de code.  En outre, l'espace de noms `My` est totalement extensible. Vous pouvez ainsi personnaliser son comportement et ajouter de nouveaux services à sa hiérarchie en fonction besoins spécifiques de votre application.  Cette rubrique présente la personnalisation des membres existants de `My` et l'ajout de vos propres classes personnalisées à cet espace de noms.  
  
 **Contenu de la rubrique**  
  
-   [Personnalisation des membres existants de l'espace de noms My](#customizing)  
  
-   [Ajout de membres aux objets My](#addingtoobjects)  
  
-   [Ajout d'objets personnalisés à l'espace de noms My](#addingcustom)  
  
-   [Ajout de membres à l'espace de noms My](#addingtonamespace)  
  
-   [Ajout d'événements aux objets personnalisés My](#addingevents)  
  
-   [Règles de conception](#design)  
  
-   [Conception de bibliothèques de classes pour My](#designing)  
  
-   [Empaquetage et déploiement d'extensions](#packaging)  
  
##  <a name="customizing"></a> Personnalisation des membres existants de l'espace de noms My  
 L'espace de noms `My` de Visual Basic expose des informations fréquemment utilisées sur votre application, votre ordinateur, etc.  Pour obtenir la liste complète des objets de l'espace de noms `My`, consultez [My Reference](../../../visual-basic/language-reference/keywords/my-reference.md).  Vous devrez peut\-être personnaliser des membres existants de l'espace de noms `My` en fonction des besoins de votre application.  La propriété d'un objet de l'espace de noms `My` qui n'est pas en lecture seule peut avoir une valeur personnalisée.  
  
 Par exemple, supposez que vous utilisez fréquemment l'objet `My.User` pour accéder au contexte de sécurité actuel de l'utilisateur exécutant votre application.  Votre société utilise toutefois un objet utilisateur personnalisé pour exposer d'autres informations et fonctions pour les utilisateurs de la société.  Dans ce scénario, vous pouvez remplacer la valeur par défaut de la propriété `My.User.CurrentPrincipal` par une instance de votre propre objet principal personnalisé, comme décrit dans l'exemple suivant.  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 La définition de la propriété `CurrentPrincipal` sur l'objet `My.User` modifie l'identité sous laquelle l'application s'exécute.  L'objet `My.User` retourne, quant à lui, des informations sur l'utilisateur récemment défini.  
  
##  <a name="addingtoobjects"></a> Ajout de membres aux objets My  
 Les types retournés par `My.Application` et `My.Computer` sont définis comme des classes `Partial`.  Vous pouvez donc étendre les objets `My.Application` et `My.Computer` en créant une classe `Partial` nommée `MyApplication` ou `MyComputer`.  La classe ne peut pas être une classe `Private`.  Si vous définissez la classe dans le cadre de l'espace de noms `My`, vous pouvez ajouter des propriétés et des méthodes qui seront incluses avec les objets `My.Application` ou `My.Computer`.  
  
 L'exemple suivant ajoute une propriété nommée `DnsServerIPAddresses` à l'objet `My.Computer` :  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> Ajout d'objets personnalisés à l'espace de noms My  
 Bien que l'espace de noms `My` fournisse des solutions pour de nombreuses tâches de programmation courantes, il est possible qu'il ne permette pas de traiter certaines tâches.  Par exemple, votre application peut accéder aux services d'annuaire personnalisés pour les données utilisateur ou utiliser des assemblys qui ne sont pas installés par défaut avec Visual Basic.  Vous pouvez étendre l'espace de noms `My` pour inclure des solutions personnalisées aux tâches courantes spécifiques à votre environnement.  L'espace de noms `My` peut être facilement étendu pour ajouter de nouveaux membres et répondre aux besoins croissants de votre application.  Par ailleurs, vous pouvez déployer vos extensions de l'espace de noms `My` aux autres développeurs comme modèle Visual Basic.  
  
###  <a name="addingtonamespace"></a> Ajout de membres à l'espace de noms My  
 Dans la mesure où `My` est un espace de noms comme les autres, vous pouvez y ajouter des propriétés de niveau supérieur en ajoutant simplement un module et en définissant un `Namespace` de type `My`.  Annotez le module avec l'attribut `HideModuleName`, comme expliqué dans l'exemple suivant.  L'attribut `HideModuleName` garantit qu'IntelliSense n'affiche pas le nom du module lorsqu'il affiche les membres de l'espace de noms `My`.  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 Pour ajouter des membres à l'espace de noms `My`, ajoutez autant de propriétés que nécessaire au module.  Pour chaque propriété ajoutée à l'espace de noms `My`, ajoutez un champ privé de type `ThreadSafeObjectProvider(Of T)`, où le type est le type retourné par votre propriété personnalisée.  Ce champ est utilisé pour créer des instances d'objet thread\-safe à retourner par la propriété en appelant la méthode `GetInstance`.  En conséquence, chaque thread qui accède à la propriété étendue reçoit sa propre instance du type retourné.  L'exemple suivant ajoute une propriété nommée `SampleExtension` de type `SampleExtension` à l'espace de noms `My` :  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> Ajout d'événements aux objets personnalisés My  
 Vous pouvez utiliser l'objet `My.Application` pour exposer des événements pour vos objets `My` personnalisés en étendant la classe partielle `MyApplication` dans l'espace de noms `My`.  Pour les projets Windows, vous pouvez double\-cliquer sur le nœud **My Project** de votre projet dans l'**Explorateur de solutions**.  Dans le **Concepteur de projets** de Visual Basic, cliquez sur l'onglet `Application`, puis sur le bouton `View Application Events`.  Un nouveau fichier nommé ApplicationEvents.vb est créé.  Il contient le code suivant, qui permet d'étendre la classe `MyApplication`.  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 Vous pouvez ajouter des gestionnaires d'événements pour vos objets `My` personnalisés en ajoutant des gestionnaires d'événements personnalisés à la classe `MyApplication`.  Les événements personnalisés vous permettent d'ajouter du code qui s'exécute lors de l'ajout ou de la suppression d'un gestionnaire d'événements ou au déclenchement de l'événement.  Notez que le code `AddHandler` d'un événement personnalisé s'exécute uniquement si un utilisateur ajoute le code permettant de gérer l'événement.  Par exemple, considérez que l'objet `SampleExtension` de la section précédente contient un événement `Load` pour lequel vous souhaitez ajouter un gestionnaire d'événements personnalisé.  L'exemple de code suivant affiche un gestionnaire d'événements personnalisé nommé `SampleExtensionLoad` qui est appelé lorsque l'événement `My.SampleExtension.Load` est déclenché.  Lors de l'ajout du code destiné à gérer le nouvel événement `My.SampleExtensionLoad`, la partie `AddHandler` de ce code d'événement personnalisé s'exécute.  La méthode `MyApplication_SampleExtensionLoad` incluse dans l'exemple de code affiche l'exemple d'un gestionnaire d'événements qui gère l'événement `My.SampleExtensionLoad`.  Notez que l'événement `SampleExtensionLoad` est disponible lorsque vous sélectionnez l'option **MyApplication Événements**  dans la liste déroulante de gauche située au\-dessus de l'éditeur de code lors de la modification du fichier ApplicationEvents.vb.  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> Règles de conception  
 Lorsque vous développez des extensions de l'espace de noms `My`, utilisez les indications suivantes afin de réduire les coûts de maintenance de vos composants d'extension.  
  
-   **Incluez uniquement la logique d'extension.** La logique incluse dans l'extension de l'espace de noms `My` doit inclure uniquement le code nécessaire pour exposer la fonctionnalité requise dans l'espace de noms `My`.  Étant donné que votre extension réside dans les projets utilisateur en tant que code source, la mise à jour du composant d'extension entraîne des coûts de maintenance élevés et doit si possible être évitée.  
  
-   **Réduisez les hypothèses de projet.** Lorsque vous créez les extensions de l'espace de noms `My`, ne supposez pas d'ensemble de références, d'importations au niveau de projet ou de paramètres de compilateur spécifiques \(par exemple, `Option Strict` désactivée\).  Réduisez plutôt les dépendances et qualifiez complètement toutes les références de type à l'aide du mot de passe `Global`.  Assurez\-vous également que l'extension est compilée avec l'option `Option Strict` activée pour limiter les erreurs dans l'extension.  
  
-   **Isolez le code d'extension.** Si vous placez le code dans un seul fichier, vous pourrez plus facilement déployer votre extension en tant que modèle d'élément Visual Studio.  Pour plus d'informations, consultez « Empaquetage et déploiement d'extensions » plus loin dans cette rubrique.  Lorsque l'ensemble du code d'extension de l'espace de noms `My` est placé dans un seul fichier ou dans un dossier séparé d'un projet, les utilisateurs pourront plus facilement localiser l'extension de l'espace de noms `My`.  
  
##  <a name="designing"></a> Conception de bibliothèques de classes pour My  
 Comme pour la plupart des modèles objet, certains modèles de design fonctionnent correctement dans l'espace de noms `My` alors que d'autres non.  Lorsque vous concevez une extension à l'espace de noms `My`, considérez les principes suivants :  
  
-   **Méthodes sans état.** Les méthodes de l'espace de noms `My` doivent fournir une solution complète à une tâche spécifique.  Assurez\-vous que les valeurs de paramètre passées à la méthode fournissent tous les éléments nécessaires pour compléter la tâche donnée.  Évitez de créer des méthodes qui dépendent d'un état antérieur, tel que des connexions ouvertes aux ressources.  
  
-   **Instances globales.** Le seul état maintenu dans l'espace de noms `My` est global pour le projet.  Par exemple, `My.Application.Info` encapsule un état partagé dans l'ensemble de l'application.  
  
-   **Types de paramètres simples.** Évitez les types de paramètres complexes.  Créez plutôt des méthodes qui n'utilisent aucune entrée de paramètre ou qui utilisent des types d'entrées simples tels que des chaînes, des types primitifs, etc.  
  
-   **Méthodes de fabrique.** Certains types sont nécessairement difficiles à instancier.  Fournir des méthodes de fabrique comme extensions de l'espace de noms `My` vous permet de détecter et d'utiliser facilement des types appartenant à cette catégorie.  Par exemple, la méthode de fabrique `My.Computer.FileSystem.OpenTextFileReader` fonctionne correctement.  Le .NET Framework contient plusieurs types de flux.  En spécifiant les fichiers texte, le `OpenTextFileReader` aide l'utilisateur à choisir le flux de données à utiliser.  
  
 Ces indications ne sont pas incompatibles avec les principes de conception généraux pour les bibliothèques de classes.  Il existe en revanche des recommandations optimisées pour les développeurs qui utilisent Visual Basic et l'espace de noms `My`.  Pour les principes de conception généraux des bibliothèques de classes, consultez [Instructions de conception d’infrastructure](../Topic/Framework%20Design%20Guidelines.md).  
  
##  <a name="packaging"></a> Empaquetage et déploiement d'extensions  
 Vous pouvez inclure des extensions de l'espace de noms `My` dans un modèle de projet Visual Studio ou bien empaqueter vos extensions et les déployer comme un modèle d'élément Visual Studio.  Lorsque vous empaquetez vos extensions de l'espace de noms `My` comme un modèle d'élément Visual Studio, vous pouvez bénéficier d'autres fonctions fournies par Visual Basic.  Ces fonctions vous permettent d'inclure une extension lorsqu'un projet fait référence à un assembly donné ou permettent aux utilisateurs d'ajouter explicitement votre extension de l'espace de noms `My` à l'aide de la page **Extensions My** du Concepteur de projets de Visual Basic.  
  
 Pour plus d'informations sur le déploiement d'extensions de l'espace de noms `My`, consultez [Packaging and Deploying Custom My Extensions](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## Voir aussi  
 [Packaging and Deploying Custom My Extensions](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Extensions My, page du Concepteur de projets](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)   
 [Page Application, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)