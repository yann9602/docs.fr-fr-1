---
title: "Walkthrough: Calling Windows APIs (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DLLs, calling"
  - "Windows API, walkthroughs"
  - "platform invoke, walkthroughs"
  - "API calls, walkthroughs [Visual Basic]"
  - "Windows API, calling"
  - "walkthroughs [Visual Basic], API calls"
  - "DllImport attribute, calling Windows API"
  - "Declare statement, declaring DLL functions"
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Walkthrough: Calling Windows APIs (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les API Windows sont des bibliothèques de liens dynamiques \(DLL, Dynamic\-Link Libraries\) qui font partie intégrante du système d'exploitation Windows.  Elles permettent d'effectuer des tâches lorsqu'il s'avère difficile d'écrire des procédures équivalentes.  Par exemple, Windows propose une fonction nommée `FlashWindowEx` qui vous permet de varier l'aspect de la barre de titre d'une application entre des tons clairs et foncés.  
  
 L'avantage de l'utilisation d'API Windows dans votre code réside dans le gain de temps de développement, car elles contiennent des douzaines de fonctions utiles déjà écrites et prêtes à être utilisées.  L'inconvénient des API Windows est qu'elles peuvent être complexes à utiliser et implacables lorsqu'une opération se déroule mal.  
  
 Les API Windows représentent une catégorie spéciale d'interopérabilité.  Les API Windows n'utilisent pas de code managé, n'ont pas de bibliothèques de types intégrées et utilisent des types de données différents de ceux utilisés avec Visual Studio.  En raison de ces différences, et comme les API Windows ne sont pas des objets COM, l'interopérabilité avec les API Windows et le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] est assurée via un appel de code non managé, ou PInvoke.  L'appel de plateforme est un service qui permet à du code managé d'appeler des fonctions non managées implémentées dans les DLL.  Pour plus d'informations, consultez [Consuming Unmanaged DLL Functions](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md).  Vous pouvez employer PInvoke en [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] en utilisant l'instruction `Declare` ou en appliquant l'attribut `DllImport` à une procédure vide.  
  
 Les appels d'API Windows représentaient auparavant une part importante de la programmation [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], mais sont rarement nécessaires avec [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)].  Dans la mesure du possible, vous devez utiliser du code managé à partir du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] plutôt que les appels d'API Windows pour effectuer des tâches.  Cette procédure pas à pas fournit des informations pour les cas dans lesquels l'utilisation des API Windows est nécessaire.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## Appels API via Declare  
 La façon la plus courante d'appeler les API Windows consiste à utiliser l'instruction `Declare`.  
  
#### Pour déclarer une procédure DLL  
  
1.  Identifiez le nom de la fonction que vous voulez appeler, ses arguments, types d'arguments et valeur de retour, ainsi que le nom et l'emplacement de la DLL qui la contient.  
  
    > [!NOTE]
    >  Pour plus d'informations sur les API Windows, consultez la documentation du kit Win32 SDK dans les API Windows du kit de développement Platform SDK.  Pour plus d'informations sur les constantes utilisées par les API Windows, examinez les fichiers d'en\-tête, tels que Windows.h, fournis avec le Kit de développement Platform SDK.  
  
2.  Ouvrez un nouveau projet d'application Windows en cliquant sur **Nouveau** dans le menu **Fichier**, puis sur **Projet**.  La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Sélectionnez **Application Windows** dans la liste des modèles de projet [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  Le nouveau projet s'affiche.  
  
4.  Ajoutez la fonction `Declare` suivante à la classe ou au module dans lequel vous souhaitez utiliser la DLL :  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### Parties de l'instruction Declare  
 L'instruction `Declare` comprend les éléments suivants.  
  
#### Modificateur Auto  
 Le modificateur `Auto` indique au runtime de convertir la chaîne basée sur le nom de la méthode en fonction des règles du Common Language Runtime \(ou du nom d'alias, s'il est indiqué\).  
  
#### Mots clés Lib et Alias  
 Le nom qui suit le mot clé `Function` est celui que votre programme utilise pour accéder à la fonction importée.  Il peut s'agir du nom réel de la fonction que vous appelez, ou vous pouvez utiliser tout nom de procédure valide, puis le mot clé `Alias` pour indiquer le nom réel de cette fonction.  
  
 Spécifiez le mot clé `Lib` suivi du nom et de l'emplacement de la DLL qui contient la fonction que vous appelez.  Vous n'avez pas besoin d'indiquer le chemin d'accès des fichiers situés dans les répertoires système Windows.  
  
 Utilisez le mot clé `Alias` si le nom de la fonction que vous appelez n'est pas un nom de procédure [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] valide ou est en conflit avec le nom d'autres éléments de votre application.  `Alias` indique le véritable nom de la fonction appelée.  
  
#### Déclaration du type de données et des arguments  
 Déclarez les arguments et leurs types de données.  Cette partie peut se révéler complexe, car les types de données utilisés dans Windows ne correspondent pas aux types de données Visual Studio.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] effectue une grande partie du travail à votre place en convertissant les arguments en types de données compatibles ; ce processus est appelé *marshaling*.  Vous pouvez contrôler de manière explicite la façon dont les arguments sont marshalés en utilisant l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> défini dans l'espace de noms <xref:System.Runtime.InteropServices>.  
  
> [!NOTE]
>  Les versions antérieures de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] vous permettent de déclarer des paramètres `As Any`, ce qui signifie que des données de n'importe quel type peuvent être utilisées.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] requiert que vous utilisiez un type de données spécifique pour toutes les instructions `Declare`.  
  
#### Constantes API Windows  
 Certains arguments sont des combinaisons de constantes.  Par exemple, l'API `MessageBox` illustrée dans cette procédure pas à pas accepte un argument de type nombre entier appelé `Typ` qui contrôle le mode d'affichage du message.  Vous pouvez déterminer la valeur numérique de ces constantes en examinant les instructions `#define` dans le fichier WinUser.h.  Les valeurs numériques sont généralement affichées au format hexadécimal ; vous pouvez donc utiliser une calculatrice pour les ajouter et les convertir au format décimal.  Par exemple, si vous voulez combiner les constantes pour le style exclamation `MB_ICONEXCLAMATION` 0x00000030 et le style Oui\/Non `MB_YESNO` 0x00000004, vous pouvez ajouter les nombres et obtenir un résultat de 0x00000034, ou 52 décimales.  Même si vous pouvez utiliser directement le résultat en décimales, il est conseillé de déclarer ces valeurs en tant que constantes dans votre application et de les combiner à l'aide de l'opérateur `Or`.  
  
###### Pour déclarer des constantes pour les appels API Windows  
  
1.  Consultez la documentation pour la fonction Windows que vous appelez.  Déterminez le nom des constantes utilisées et le nom du fichier .h qui contient les valeurs numériques de ces constantes.  
  
2.  Utilisez un éditeur de texte, tel que le Bloc\-notes, pour afficher le contenu du fichier d'en\-tête .h et rechercher les valeurs associées aux constantes que vous utilisez.  Par exemple, l'API `MessageBox` utilise la constante `MB_ICONQUESTION` pour afficher un point d'interrogation dans le message.  La définition de `MB_ICONQUESTION` se trouve dans WinUser.h et est définie comme suit :  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Ajoutez des instructions `Const` équivalentes pour votre classe ou votre module pour rendre ces constantes disponibles pour l'application.  Par exemple :  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### Pour appeler la procédure DLL  
  
1.  Ajoutez un bouton nommé `Button1` au formulaire de départ de votre projet, puis double\-cliquez dessus pour afficher son code.  Le gestionnaire d'événements du bouton s'affiche.  
  
2.  Ajoutez du code au gestionnaire d'événements `Click` pour le bouton que vous avez ajouté pour appeler la procédure et indiquez les arguments appropriés :  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  Exécutez le projet en appuyant sur F5.  Le message s'affiche avec les deux boutons de réponse **Oui** et **Non**.  Cliquez sur l'un des deux.  
  
#### Marshaling de données  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] convertit automatiquement les types de données des paramètres et des valeurs de retour pour les appels d'API Windows, mais vous pouvez utiliser l'attribut `MarshalAs` pour indiquer de façon explicite les types de données non managés attendus par une API.  Pour plus d'informations sur le marshaling d'interopérabilité, consultez [Interop Marshaling](../Topic/Interop%20Marshaling.md).  
  
###### Pour utiliser Declare et MarshalAs dans un appel API  
  
1.  Déterminez le nom de la fonction à appeler, ses arguments, types de données et valeur de retour.  
  
2.  Pour simplifier l'accès à l'attribut `MarshalAs`, ajoutez une instruction `Imports` en haut du code de la classe ou du module, comme dans l'exemple suivant :  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  Ajoutez un prototype de fonction pour la fonction importée à la classe ou au module que vous utilisez et appliquez l'attribut `MarshalAs` aux paramètres ou à la valeur de retour.  Dans l'exemple suivant, un appel API qui attend le type `void*` est marshalé en tant que `AsAny` :  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## Appels API via DllImport  
 L'attribut `DllImport` offre un deuxième moyen pour appeler des fonctions dans les DLL sans bibliothèque de types.  `DllImport` équivaut à peu près à une instruction `Declare`, mais permet de mieux contrôler la façon dont les fonctions sont appelées.  
  
 Vous pouvez utiliser `DllImport` avec la plupart des appels API Windows tant que l'appel fait référence à une méthode partagée \(parfois appelée *statique*\).  Vous ne pouvez pas utiliser des méthodes qui nécessitent une instance d'une classe.  À la différence des instructions `Declare`, les appels `DllImport` ne peuvent pas utiliser l'attribut `MarshalAs`.  
  
#### Pour appeler une API Windows à l'aide de l'attribut DllImport  
  
1.  Ouvrez un nouveau projet d'application Windows en cliquant sur **Nouveau** dans le menu **Fichier**, puis sur **Projet**.  La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Sélectionnez **Application Windows** dans la liste des modèles de projet [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  Le nouveau projet s'affiche.  
  
3.  Ajoutez un bouton nommé `Button2` au formulaire de départ.  
  
4.  Double\-cliquez sur `Button2` pour ouvrir le mode code pour le formulaire.  
  
5.  Pour simplifier l'accès à `DllImport`, ajoutez une instruction `Imports` en haut du code de la classe du formulaire de départ :  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  Déclarez une fonction vide qui précède l'instruction `End Class` pour le formulaire et affectez à la fonction le nom `MoveFile`.  
  
7.  Appliquez les modificateurs `Public` et `Shared` à la déclaration de fonction et définissez des paramètres pour `MoveFile` en fonction des arguments que la fonction API Windows utilise :  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     Votre fonction peut porter n'importe quel nom de procédure valide ; l'attribut `DllImport` indique le nom dans la DLL.  Il gère également le marshaling d'interopérabilité pour les paramètres et valeurs de retour ; vous pouvez donc choisir des types de données Visual Studio similaires à ceux que l'API utilise.  
  
8.  Appliquez l'attribut `DllImport` à la fonction vide.  Le premier paramètre représente le nom et l'emplacement de la DLL qui contient la fonction que vous appelez.  Vous n'avez pas besoin d'indiquer le chemin d'accès des fichiers situés dans les répertoires système Windows.  Le second paramètre est un argument nommé qui indique le nom de la fonction dans API Windows :  Dans cet exemple, l'attribut `DllImport` force les appels à `MoveFile` à être transférés à `MoveFileW` dans KERNEL32.DLL.  La méthode `MoveFileW` copie un fichier à partir du chemin d'accès `src` vers le chemin d'accès `dst`.  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. Ajoutez le code au gestionnaire d'événements `Button2_Click` pour appeler la fonction :  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Créez un fichier nommé Test.txt et placez\-le dans le répertoire C:\\Tmp de votre disque dur.  Créez le répertoire Tmp si nécessaire.  
  
11. Appuyez sur F5 pour démarrer l'application.  Le formulaire principal s'affiche.  
  
12. Cliquez sur **Button2**.  Le message "The file was moved successfully" s'affiche si le fichier peut être déplacé.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Creating Prototypes in Managed Code](../Topic/Creating%20Prototypes%20in%20Managed%20Code.md)   
 [Marshaling a Delegate as a Callback Method](../Topic/Marshaling%20a%20Delegate%20as%20a%20Callback%20Method.md)