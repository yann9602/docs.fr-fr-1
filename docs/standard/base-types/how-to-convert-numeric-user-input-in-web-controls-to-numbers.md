---
title: "Comment : convertir des entrées d'utilisateur numériques figurant dans des contrôles Web en nombres"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92e28e3b303a7523b9da69b7eb283e0261fc681c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Comment : convertir des entrées d'utilisateur numériques figurant dans des contrôles Web en nombres
Comme une page Web peut être affichée n’importe où dans le monde, les utilisateurs peuvent entrer des données numériques dans un <xref:System.Web.UI.WebControls.TextBox> contrôle dans un nombre presque illimité de formats. Par conséquent, il est très important de déterminer les paramètres régionaux et la culture de l’utilisateur de la page Web. Lorsque vous analysez l’entrée d’utilisateur, vous pouvez ensuite appliquer les conventions de mise en forme définies par les paramètres régionaux et la culture de l’utilisateur.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Convertir l’entrée numérique à partir d’un contrôle TextBox Web à un nombre  
  
1.  Déterminez si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriété est remplie. Si elle n’est pas le cas, passez à l’étape 6.  
  
2.  Si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété est remplie, récupérez son premier élément. Le premier élément indique l’utilisateur par défaut ou langue et région.  
  
3.  Instancier une <xref:System.Globalization.CultureInfo> objet qui représente l’utilisateur de culture par défaut en appelant le <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> constructeur.  
  
4.  Appelez le `TryParse` ou `Parse` d’entrée de méthode du type numérique que vous souhaitez convertir l’utilisateur à. Utilisez une surcharge de la `TryParse` ou `Parse` méthode avec un `provider` paramètre et lui passer une des opérations suivantes :  
  
    -   Le <xref:System.Globalization.CultureInfo> objet créé à l’étape 3.  
  
    -   Le <xref:System.Globalization.NumberFormatInfo> objet qui est retourné par la <xref:System.Globalization.CultureInfo.NumberFormat%2A> propriété de la <xref:System.Globalization.CultureInfo> objet créé à l’étape 3.  
  
5.  Si la conversion échoue, répétez les étapes 2 à 4 pour chaque élément restant dans le tableau de chaînes retournés par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété.  
  
6.  Si la conversion échoue encore ou si le tableau de chaînes retourné par la <xref:System.Web.HttpRequest.UserLanguages%2A> propriété est vide, d’analyser la chaîne à l’aide de la culture dite indifférente, qui est retourné par la <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriété.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant est la page code-behind complète d’un formulaire Web qui invite l’utilisateur à entrer une valeur numérique dans un <xref:System.Web.UI.WebControls.TextBox> de contrôle et la convertit en un nombre. Ce nombre est ensuite doublé et affiché en utilisant les mêmes règles de mise en forme en tant que l’entrée d’origine.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 Le <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> propriété est remplie par les noms de culture qui figurent dans `Accept-Language` en-têtes inclus dans une requête HTTP. Toutefois, certains navigateurs n’incluent `Accept-Language` en-têtes dans leurs demandes et les utilisateurs peuvent également supprimer complètement les en-têtes. Il est donc important d’avoir une culture de secours lors de l’analyse de l’entrée d’utilisateur. En règle générale, la culture de secours est la culture dite indifférente retournée par <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Les utilisateurs peuvent également fournir Internet Explorer avec des noms de cultures qu’ils entrent dans une zone de texte, il peut arriver que les noms de cultures n’est peut-être pas valides. Il est donc important d’utiliser la gestion des exceptions lorsque vous instanciez un <xref:System.Globalization.CultureInfo> objet.  
  
 Lorsque récupérées à partir d’une requête HTTP soumise par Internet Explorer, le <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> tableau est rempli par ordre de préférence de l’utilisateur. Le premier élément du tableau contient le nom de culture/région principale de l’utilisateur. Si le tableau contient des éléments supplémentaires, Internet Explorer leur assigne arbitrairement un spécificateur de qualité, qui est délimité par un point-virgule à partir du nom de culture. Par exemple, une entrée pour la culture fr-FR peut prendre la forme `fr-FR;q=0.7`.  
  
 L’exemple appelle la <xref:System.Globalization.CultureInfo.%23ctor%2A> constructeur avec son `useUserOverride` paramètre la valeur `false` pour créer un nouveau <xref:System.Globalization.CultureInfo> objet. Cela garantit que, si le nom de culture est le nom de culture par défaut sur le serveur, la nouvelle <xref:System.Globalization.CultureInfo> objet créé par le constructeur de classe contient les paramètres par défaut d’une culture et ne reflète pas les paramètres de substitution à l’aide du serveur  **Régional et Options de langue** application. Les valeurs des paramètres substitués sur le serveur sont peu susceptibles d’exister sur le système de l’utilisateur ou qu’elles apparaissent dans l’entrée d’utilisateur.  
  
 Votre code peut appeler le `Parse` ou `TryParse` sera convertie en méthode de type numérique de l’entrée d’utilisateur. Les appels répétés à une méthode d’analyse peuvent être nécessaire pour une opération d’analyse unique. Par conséquent, le `TryParse` méthode est préférable, car elle retourne `false` si une opération d’analyse échoue. En revanche, la gestion des exceptions répétées pouvant être levées par le `Parse` méthode peut être très coûteux dans une application Web.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler le code, copiez-le dans un [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page code-behind afin qu’il remplace tout le code existant. Le [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page Web doit contenir les contrôles suivants :  
  
-   A <xref:System.Web.UI.WebControls.Label> contrôle, qui n’est pas référencé dans le code. Définir son <xref:System.Web.UI.WebControls.TextBox.Text%2A> propriété « Entrez un nombre : ».  
  
-   un contrôle <xref:System.Web.UI.WebControls.TextBox> nommé `NumericString` ;  
  
-   un contrôle <xref:System.Web.UI.WebControls.Button> nommé `OKButton` ; Définir son <xref:System.Web.UI.WebControls.Button.Text%2A> propriété sur « OK ».  
  
 Modifier le nom de la classe à partir de `NumericUserInput` au nom de la classe qui est définie par le `Inherits` attribut de la [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] la page `Page` la directive. Modifier le nom de la `NumericInput` référence au nom défini par l’objet le `id` attribut de la [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] la page `form` balise.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour empêcher un utilisateur d’injection de script dans le flux de données HTML, l’entrée d’utilisateur doit jamais être répétée directement dans la réponse du serveur. Au lieu de cela, il doit être encodé à l’aide de la <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Analyse de chaînes numériques](../../../docs/standard/base-types/parsing-numeric.md)
