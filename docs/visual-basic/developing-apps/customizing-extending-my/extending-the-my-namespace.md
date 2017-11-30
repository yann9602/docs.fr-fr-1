---
title: Extension de l'espace de noms My dans Visual Basic
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25fff04b19cce299a2d437e662fb7481153d29da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Extension de l'espace de noms My dans Visual Basic
Le `My` espace de noms dans Visual Basic expose des propriétés et méthodes qui vous permettent de tirer facilement parti de la puissance du .NET Framework. Le `My` espace de noms simplifie les problèmes de programmation courants qui réduisent souvent difficile à une seule ligne de code. En outre, le `My` espace de noms est totalement extensible afin que vous pouvez personnaliser le comportement de `My` et ajouter de nouveaux services à sa hiérarchie pour s’adapter aux besoins de l’application spécifique. Cette rubrique décrit comment personnaliser des membres existants de la `My` espace de noms et comment ajouter vos propres classes personnalisées pour le `My` espace de noms.  
  
 **Contenu de la rubrique**  
  
-   [Personnalisation des membres de mon Namespace existants](#customizing)  
  
-   [Ajout de membres aux objets My](#addingtoobjects)  
  
-   [Ajout d’objets personnalisés à la My Namespace](#addingcustom)  
  
-   [Ajout de membres à la My Namespace](#addingtonamespace)  
  
-   [Ajout d’événements aux objets personnalisés My](#addingevents)  
  
-   [Règles de conception](#design)  
  
-   [Conception de bibliothèques de classes pour My](#designing)  
  
-   [Empaquetage et déploiement des Extensions](#packaging)  
  
##  <a name="customizing"></a>Personnalisation des membres de mon Namespace existants  
 Le `My` espace de noms dans Visual Basic expose informations fréquemment utilisées sur votre application, votre ordinateur et bien plus encore. Pour obtenir la liste complète des objets dans le `My` espace de noms, consultez [My Reference](../../../visual-basic/language-reference/keywords/my-reference.md). Vous devrez peut-être personnaliser des membres existants de la `My` espace de noms afin qu’ils mieux répondre aux besoins de votre application. N’importe quelle propriété d’un objet dans le `My` espace de noms qui n’est pas en lecture seule peut être défini sur une valeur personnalisée.  
  
 Par exemple, supposez que vous utilisez fréquemment le `My.User` objet pour accéder au contexte de sécurité actuel pour l’utilisateur qui exécute votre application. Toutefois, votre entreprise utilise un objet utilisateur personnalisé pour exposer des informations supplémentaires et des fonctionnalités pour les utilisateurs au sein de la société. Dans ce scénario, vous pouvez remplacer la valeur par défaut de la `My.User.CurrentPrincipal` propriété avec une instance de votre propre objet principal personnalisé, comme indiqué dans l’exemple suivant.  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 Définition de la `CurrentPrincipal` propriété sur le `My.User` objet modifie l’identité sous laquelle l’application s’exécute. Le `My.User` objet, à son tour, retourne plus d’informations sur l’utilisateur qui vient d’être spécifié.  
  
##  <a name="addingtoobjects"></a>Ajout de membres aux objets My  
 Les types retournés par `My.Application` et `My.Computer` sont définies comme `Partial` classes. Par conséquent, vous pouvez étendre le `My.Application` et `My.Computer` objets en créant un `Partial` classe nommée `MyApplication` ou `MyComputer`. La classe ne peut pas être un `Private` classe. Si vous spécifiez la classe dans le cadre de la `My` espace de noms, vous pouvez ajouter méthodes et propriétés qui seront inclus dans le `My.Application` ou `My.Computer` objets.  
  
 Par exemple, l’exemple suivant ajoute une propriété nommée `DnsServerIPAddresses` à la `My.Computer` objet.  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a>Ajout d’objets personnalisés à la My Namespace  
 Bien que le `My` espace de noms fournit des solutions pour de nombreuses tâches de programmation courantes, vous pouvez rencontrer des tâches qui le `My` espace de noms ne traite pas. Par exemple, votre application peut accéder aux services d’annuaire personnalisés pour les données utilisateur ou votre application peut utiliser des assemblys qui ne sont pas installés par défaut avec Visual Basic. Vous pouvez étendre le `My` espace de noms à inclure des solutions personnalisées pour les tâches courantes qui sont spécifiques à votre environnement. Le `My` espace de noms peut facilement être étendu pour ajouter de nouveaux membres pour répondre aux besoins croissants de l’application. En outre, vous pouvez déployer votre `My` extensions de l’espace de noms à d’autres développeurs comme modèle Visual Basic.  
  
###  <a name="addingtonamespace"></a>Ajout de membres à la My Namespace  
 Étant donné que `My` est un espace de noms comme n’importe quel autre espace de noms, vous pouvez ajouter des propriétés de niveau supérieur à ce dernier en ajoutant un module et en spécifiant simplement un `Namespace` de `My`. Annotez le module avec le `HideModuleName` d’attributs comme indiqué dans l’exemple suivant. Le `HideModuleName` attribut garantit que les IntelliSense n’affichera pas le nom du module lorsqu’il affiche les membres de le `My` espace de noms.  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 Pour ajouter des membres à la `My` espace de noms, ajouter des propriétés selon les besoins pour le module. Pour chaque propriété ajoutée à la `My` espace de noms, ajoutez un champ privé de type `ThreadSafeObjectProvider(Of T)`, où le type est le type retourné par votre propriété personnalisée. Ce champ est utilisé pour créer des instances d’objet thread-safe doivent être retournées par la propriété en appelant le `GetInstance` (méthode). Par conséquent, chaque thread qui accède à la propriété étendue reçoit sa propre instance du type retourné. L’exemple suivant ajoute une propriété nommée `SampleExtension` qui est de type `SampleExtension` à la `My` espace de noms :  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a>Ajout d’événements aux objets personnalisés My  
 Vous pouvez utiliser la `My.Application` objet d’exposer des événements pour votre personnalisé `My` objets en étendant le `MyApplication` classe partielle dans le `My` espace de noms. Pour les projets basés sur Windows, vous pouvez double-cliquer sur le **mon projet** nœud de votre projet dans **l’Explorateur de solutions**. Dans Visual Basic **Concepteur de projets**, cliquez sur le `Application` onglet, puis cliquez sur le `View Application Events` bouton. Un nouveau fichier nommé ApplicationEvents.vb sera créé. Il contient le code suivant pour étendre la `MyApplication` classe.  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 Vous pouvez ajouter des gestionnaires d’événements pour votre personnalisé `My` objets en ajoutant des gestionnaires d’événements personnalisés à la `MyApplication` classe. Événements personnalisés permettent d’ajouter du code qui s’exécute quand un gestionnaire d’événements est ajouté, supprimé, ou l’événement est déclenché. Notez que le `AddHandler` de code pour un événement personnalisé s’exécute uniquement si le code est ajouté par l’utilisateur pour gérer l’événement. Par exemple, considérez que la `SampleExtension` objet à partir de la section précédente a une `Load` événement que vous souhaitez ajouter un gestionnaire d’événements personnalisé. L’exemple de code suivant montre un gestionnaire d’événements personnalisé nommé `SampleExtensionLoad` qui sera appelé lorsque le `My.SampleExtension.Load` événement se produit. Lorsque le code est ajouté pour gérer le nouveau `My.SampleExtensionLoad` événement, la `AddHandler` partie de ce code d’événement personnalisé est exécuté. Le `MyApplication_SampleExtensionLoad` (méthode) est incluse dans l’exemple de code pour afficher un exemple de gestionnaire d’événements qui gère le `My.SampleExtensionLoad` événement. Notez que la `SampleExtensionLoad` événements seront disponibles lorsque vous sélectionnez le **événements** option dans la liste déroulante gauche au-dessus de l’éditeur de Code lorsque vous modifiez le fichier ApplicationEvents.vb.  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a>Règles de conception  
 Lorsque vous développez des extensions du `My` espace de noms, utilisez les instructions suivantes pour aider à réduire les coûts de maintenance de vos composants d’extension.  
  
-   **Inclure uniquement la logique d’extension.** La logique incluse dans le `My` extension de l’espace de noms doit inclure uniquement le code qui est nécessaire pour exposer la fonctionnalité requise dans le `My` espace de noms. Étant donné que votre extension réside dans les projets utilisateur en tant que code source, le composant d’extension de mise à jour implique un coût de maintenance élevés et doit être évitée si possible.  
  
-   **Réduisez les hypothèses de projet.** Lorsque vous créez vos extensions de le `My` espace de noms, ne supposez pas un ensemble de références, importations au niveau du projet ou de paramètres de compilateur spécifiques (par exemple, `Option Strict` off). Au lieu de cela, réduisez les dépendances et qualifier complètement toutes les références de type à l’aide de la `Global` (mot clé). En outre, assurez-vous que l’extension est compilée avec `Option Strict` on pour réduire les erreurs dans l’extension.  
  
-   **Isolez le code d’extension.** Placer le code dans un seul fichier rend votre extension facilement déployables sous la forme d’un modèle d’élément Visual Studio. Pour plus d’informations, consultez « Empaquetage et déploiement d’Extensions » plus loin dans cette rubrique. Placer tous les le `My` code d’extension espace de noms dans un seul fichier ou un dossier distinct dans un projet sera également aider les utilisateurs à localiser le `My` extension de l’espace de noms.  
  
##  <a name="designing"></a>Conception de bibliothèques de classes pour My  
 Comme c’est le cas avec la plupart des modèles objet, certains modèles de design fonctionnent correctement dans le `My` espace de noms et d’autres ne le font pas. Lorsque vous concevez une extension à la `My` espace de noms, considérez les principes suivants :  
  
-   **Méthodes sans état.** Méthodes dans le `My` espace de noms doit fournir une solution complète pour une tâche spécifique. Assurez-vous que les valeurs de paramètre qui sont passés à la méthode fournissent toutes les entrées nécessaires pour terminer la tâche particulière. Évitez de créer des méthodes qui s’appuient sur l’état antérieur, telles que les connexions ouvertes aux ressources.  
  
-   **Instances globales.** Le seul état qui est conservé dans le `My` espace de noms est global pour le projet. Par exemple, `My.Application.Info` encapsule l’état partagé dans l’ensemble de l’application.  
  
-   **Types de paramètres simples.** Garder les choses simples en évitant les types de paramètres complexes. Au lieu de cela, créez des méthodes qui n’utilisent pas de paramètre d’entrée, ou qui acceptent des types d’entrées simples tels que des chaînes, les types primitifs et ainsi de suite.  
  
-   **Méthodes de fabrique.** Certains types sont nécessairement difficiles à instancier. Fournir des méthodes de fabrique comme extensions le `My` espace de noms vous permet de découvrir plus facilement et de consommer des types qui appartiennent à cette catégorie. Est un exemple d’une méthode de fabrique qui fonctionne bien `My.Computer.FileSystem.OpenTextFileReader`. Il existe plusieurs types de flux de données dans le .NET Framework. En spécifiant des fichiers texte en particulier, le `OpenTextFileReader` permet à l’utilisateur de comprendre le flux à utiliser.  
  
 Ces instructions n’empêchent pas les principes de conception généraux pour les bibliothèques de classes. Au lieu de cela, ils sont des recommandations qui sont optimisées pour les développeurs qui utilisent Visual Basic et le `My` espace de noms. Pour les principes de conception générales pour la création de bibliothèques de classes, consultez [les règles de conception de Framework](../../../standard/design-guidelines/index.md).  
  
##  <a name="packaging"></a>Empaquetage et déploiement des Extensions  
 Vous pouvez inclure `My` extensions de l’espace de noms dans un modèle de projet Visual Studio, ou vous pouvant empaqueter vos extensions et les déployer comme un modèle d’élément Visual Studio. Lorsque vous empaquetez votre `My` extensions de l’espace de noms comme un modèle d’élément Visual Studio, vous pouvez tirer parti de fonctionnalités supplémentaires fournies par Visual Basic. Ces fonctionnalités vous permettent d’inclure une extension lorsqu’un projet fait référence à un assembly particulier, ou permettre aux utilisateurs d’ajouter explicitement votre `My` extension de l’espace de noms à l’aide de la **Extensions My** page de Visual Basic Concepteur de projets.  
  
 Pour plus d’informations sur le déploiement `My` extensions de l’espace de noms, consultez [empaquetage et déploiement des Extensions My personnalisées](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement des extensions My personnalisées](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 [Extension du modèle d’application Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [Personnalisation de la disponibilité ou non des objets dans My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Extensions My, Page du Concepteur de projets](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)  
 [Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
