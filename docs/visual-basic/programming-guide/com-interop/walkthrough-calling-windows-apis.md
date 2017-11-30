---
title: "Procédure pas à pas : appel des API Windows (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d494ad0f8bd4eb0dac57de214064fd2d208011ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a>Procédure pas à pas : appel des API Windows (Visual Basic)
API Windows sont des bibliothèques de liens dynamiques (DLL) qui font partie du système d’exploitation Windows. Elles permettent d’effectuer des tâches lorsqu’il est difficile d’écrire des procédures équivalentes de votre choix. Par exemple, Windows propose une fonction nommée `FlashWindowEx` qui permet d’effectuer la barre de titre d’une application en alternant clairs et foncés.  
  
 L’avantage de l’utilisation des API Windows dans votre code, qu’ils peuvent enregistrer des temps de développement, car ils contiennent des dizaines de fonctions utiles qui sont déjà écrit et prêtes à être utilisées. L’inconvénient est que les API Windows peut être difficiles à utiliser et envoyés de cas de problème.  
  
 Les API Windows représentent une catégorie spéciale d’interopérabilité. API Windows n’utilisent pas de code managé, n’ont pas intégrées de bibliothèques de types et utiliser des types de données qui sont différents de ceux utilisés avec Visual Studio. En raison de ces différences, et parce que l’API Windows ne sont pas des objets COM, l’interopérabilité avec les API Windows et le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] est effectuée à l’aide de la plateforme de code non managé, ou PInvoke. Appel de plateforme est un service qui permet de code managé d’appeler des fonctions non managées implémentées dans des DLL. Pour plus d’informations, consultez [consommation de fonctions DLL non managées](../../../framework/interop/consuming-unmanaged-dll-functions.md). Vous pouvez utiliser PInvoke dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] à l’aide la `Declare` instruction ou en appliquant la `DllImport` d’attribut à une procédure vide.  
  
 Appels d’API Windows ont été une partie importante de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] de programmation dans le passé, mais sont rarement nécessaires avec Visual Basic .NET. Chaque fois que possible, vous devez utiliser du code managé à partir de la [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pour effectuer des tâches, au lieu d’appels d’API Windows. Cette procédure pas à pas fournit des informations pour les cas dans lesquels l’utilisation des API Windows est nécessaire.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a>Déclarent des appels d’API à l’aide de  
 La méthode la plus courante pour appeler des API Windows est à l’aide de la `Declare` instruction.  
  
#### <a name="to-declare-a-dll-procedure"></a>Pour déclarer une procédure DLL  
  
1.  Déterminer le nom de la fonction que vous souhaitez appeler, ainsi que ses arguments, les types d’arguments et retourne une valeur, ainsi que le nom et l’emplacement de la DLL qui la contient.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les API Windows, consultez la documentation du SDK Win32 dans l’API du Kit de développement Platform SDK Windows. Pour plus d’informations sur les constantes que vous utilisez des API Windows, examinez les fichiers d’en-tête tels que Windows.h inclus avec le SDK de plateforme.  
  
2.  Ouvrez un nouveau projet d’Application Windows en cliquant sur **nouveau** sur la **fichier** menu, puis en cliquant sur **projet**. La boîte de dialogue **Nouveau projet** s’affiche.  
  
3.  Sélectionnez **Application Windows** dans la liste des [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] modèles de projet. Le nouveau projet s’affiche.  
  
4.  Ajoutez le code suivant `Declare` de fonction à la classe ou le module dans lequel vous souhaitez utiliser la DLL :  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a>Parties de l’instruction Declare  
 La `Declare` instruction inclut les éléments suivants.  
  
#### <a name="auto-modifier"></a>Modificateur Auto  
 Le `Auto` modificateur indique au runtime de convertir la chaîne basée sur le nom de la méthode en fonction des règles du common language runtime (ou nom d’alias si spécifié).  
  
#### <a name="lib-and-alias-keywords"></a>Mots clés lib et Alias  
 Le nom qui suit le `Function` mot clé est le nom de votre programme utilise pour accéder à la fonction importée. Il peut être le même que le nom réel de la fonction que vous appelez, ou vous pouvez utiliser n’importe quel nom de procédure valide, un puis le `Alias` mot clé pour spécifier le nom réel de la fonction que vous appelez.  
  
 Spécifiez le `Lib` (mot clé), suivi par le nom et l’emplacement de la DLL qui contient la fonction que vous appelez. Vous n’avez pas besoin de spécifier le chemin d’accès pour les fichiers situés dans les répertoires de système de Windows.  
  
 Utilisez le `Alias` mot clé si le nom de la fonction que vous appelez n’est pas valide [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nom de la procédure, ou est en conflit avec le nom d’autres éléments dans votre application. `Alias`Indique le véritable nom de la fonction appelée.  
  
#### <a name="argument-and-data-type-declarations"></a>Argument et les déclarations de Type de données  
 Déclarez les arguments et leurs types de données. Cette partie peut être complexe, car les types de données que Windows utilise ne correspondent pas aux types de données Visual Studio. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]effectue une grande partie du travail pour vous, en convertissant les arguments en types de données compatibles, un processus appelé *marshaling*. Vous pouvez contrôler explicitement la façon dont les arguments sont marshalés en utilisant le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut défini dans le <xref:System.Runtime.InteropServices> espace de noms.  
  
> [!NOTE]
>  Les versions précédentes de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] autorisées vous permet de déclarer des paramètres `As Any`, ce qui signifie que des données de toutes les données de type peut être utilisé. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]exige que vous utilisiez un type de données spécifique pour toutes les `Declare` instructions.  
  
#### <a name="windows-api-constants"></a>Constantes de l’API Windows  
 Certains arguments sont des combinaisons de constantes. Par exemple, le `MessageBox` API indiqué dans cette procédure pas à pas accepte un argument entier appelé `Typ` qui contrôle l’affichage de la boîte de message. Vous pouvez déterminer la valeur numérique de ces constantes en examinant le `#define` instructions dans le fichier WinUser.h. Les valeurs numériques sont généralement affichées au format hexadécimal, vous pouvez donc utiliser une calculatrice pour les ajouter et convertir en nombre décimal. Par exemple, si vous souhaitez combiner les constantes pour le style exclamation `MB_ICONEXCLAMATION` 0 x 00000030 et la valeur Oui/aucun style `MB_YESNO` 0 x 00000004, vous pouvez ajouter les nombres et obtenir un résultat de 0 x 00000034, ou 52 décimales. Vous pouvez utiliser le résultat en décimales directement, il est préférable de déclarer ces valeurs en tant que constantes dans votre application et de les associer à l’aide de la `Or` opérateur.  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a>Pour déclarer des constantes pour les appels d’API Windows  
  
1.  Consultez la documentation de la fonction Windows que vous appelez. Déterminer le nom de l’une des constantes qu’il utilise et le nom du fichier .h qui contient les valeurs numériques de ces constantes.  
  
2.  Utilisez un éditeur de texte, tel que le bloc-notes, pour afficher le contenu du fichier d’en-tête (.h) et rechercher les valeurs associées aux constantes que vous utilisez. Par exemple, le `MessageBox` API utilise la constante `MB_ICONQUESTION` pour afficher un point d’interrogation dans la boîte de message. La définition de `MB_ICONQUESTION` dans WinUser.h et est comme suit :  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  Ajouter équivalent `Const` instructions à votre classe ou module pour rendre ces constantes disponibles pour votre application. Exemple :  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a>Pour appeler la procédure DLL  
  
1.  Ajoutez un bouton nommé `Button1` au démarrage de l’écran de votre projet, puis double-cliquez dessus pour afficher son code. Le Gestionnaire d’événements pour le bouton s’affiche.  
  
2.  Ajoutez le code pour le `Click` Gestionnaire d’événements pour le bouton que vous avez ajouté pour appeler la procédure et indiquez les arguments appropriés :  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  Exécutez le projet en appuyant sur F5. La boîte de message s’affiche avec les deux **Oui** et **non** boutons de réponse. Cliquez sur l’une.  
  
#### <a name="data-marshaling"></a>Marshaling de données  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Convertit les types de données des paramètres et valeurs de retour pour les appels d’API Windows, mais vous pouvant utiliser automatiquement les `MarshalAs` attribut pour spécifier explicitement les types de données non managés attendus par une API. Pour plus d’informations sur le marshaling d’interopérabilité, consultez [Marshaling d’interopérabilité](../../../framework/interop/interop-marshaling.md).  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a>Pour utiliser Declare et MarshalAs dans un appel d’API  
  
1.  Déterminer le nom de la fonction que vous souhaitez appeler, ses arguments, les types de données, et la valeur de retour.  
  
2.  Pour simplifier l’accès à la `MarshalAs` d’attribut, ajoutez un `Imports` en haut du code pour la classe ou un module, comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  Ajouter un prototype de fonction pour la fonction importée à la classe ou le module que vous utilisez et appliquez le `MarshalAs` aux paramètres d’attribut ou la valeur de retour. Dans l’exemple suivant, un appel API qui attend le type `void*` est marshalé en tant que `AsAny`:  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a>Appels d’API à l’aide de DllImport  
 Le `DllImport` attribut fournit un deuxième moyen pour appeler des fonctions dans les DLL sans bibliothèques de types. `DllImport`équivaut à peu près à utiliser un `Declare` instruction mais fournit plus de contrôle sur la façon dont les fonctions sont appelées.  
  
 Vous pouvez utiliser `DllImport` avec la plupart des API Windows appelle tant que l’appel fait référence à un élément partagé (parfois appelé *statique*) méthode. Vous ne pouvez pas utiliser les méthodes qui requièrent une instance d’une classe. Contrairement aux `Declare` instructions, `DllImport` appels ne peut pas utiliser le `MarshalAs` attribut.  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a>Pour appeler une API Windows à l’aide de l’attribut DllImport  
  
1.  Ouvrez un nouveau projet d’Application Windows en cliquant sur **nouveau** sur la **fichier** menu, puis en cliquant sur **projet**. La boîte de dialogue **Nouveau projet** s’affiche.  
  
2.  Sélectionnez **Application Windows** dans la liste des [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] modèles de projet. Le nouveau projet s’affiche.  
  
3.  Ajoutez un bouton nommé `Button2` à l’écran de démarrage.  
  
4.  Double-cliquez sur `Button2` pour afficher le code du formulaire.  
  
5.  Pour simplifier l’accès à `DllImport`, ajoutez une `Imports` en haut du code pour la classe de formulaire de démarrage :  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  Déclarez une fonction vide qui précède le `End Class` instruction pour le formulaire et le nom de la fonction `MoveFile`.  
  
7.  Appliquer le `Public` et `Shared` modificateurs de la déclaration de fonction et définir les paramètres pour `MoveFile` basées sur les arguments de la fonction API Windows utilise :  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     Votre fonction peut avoir n’importe quel nom de procédure valide ; le `DllImport` attribut spécifie le nom de la DLL. Il gère également le marshaling d’interopérabilité pour les paramètres et l’API utilise des types de valeurs de retour, vous pouvez donc choisir des types de données de Visual Studio qui sont similaires aux données.  
  
8.  Appliquer le `DllImport` d’attribut à la fonction vide. Le premier paramètre est le nom et l’emplacement de la DLL qui contient la fonction que vous appelez. Vous n’avez pas besoin de spécifier le chemin d’accès pour les fichiers situés dans les répertoires de système de Windows. Le deuxième paramètre est un argument nommé qui spécifie le nom de la fonction dans l’API Windows. Dans cet exemple, le `DllImport` attribut force les appels à `MoveFile` à transmettre à `MoveFileW` dans KERNEL32. DLL. Le `MoveFileW` méthode copie un fichier à partir du chemin `src` pour le chemin d’accès `dst`.  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. Ajoutez le code pour le `Button2_Click` Gestionnaire d’événements à appeler la fonction :  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. Créez un fichier nommé Test.txt et placez-le dans le répertoire C:\Tmp de votre disque dur. Créez le répertoire Tmp si nécessaire.  
  
11. Appuyez sur F5 pour démarrer l'application. Le formulaire principal s’affiche.  
  
12. Cliquez sur **Button2**. Le message « le fichier a été déplacé avec succès » s’affiche si le fichier peut être déplacé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Alias](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Création de prototypes dans du code managé](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [Marshaling d’un délégué comme méthode de rappel](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
