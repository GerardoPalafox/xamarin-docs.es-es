---
title: Temas de Xamarin.Forms
description: Este artículo presenta los temas de Xamarin.Forms, que definen la apariencia visual específico para las vistas estándares.
ms.prod: xamarin
ms.assetid: 3DFB7C55-69F6-4980-A501-588719143482
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 09/01/2017
ms.openlocfilehash: 1c5b2635dca6aa74fd0dfb92d7e62e6da3140538
ms.sourcegitcommit: be6f6a8f77679bb9675077ed25b5d2c753580b74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051113"
---
# <a name="xamarinforms-themes"></a>Temas de Xamarin.Forms

[![Descargar ejemplo](~/media/shared/download.png) descargar el ejemplo](https://github.com/xamarin/xamarin-forms-samples/tree/master/Themes/ThemesDemo)

![](~/media/shared/preview.png "Esta API está actualmente en versión preliminar")

Los temas de Xamarin.Forms se anunciaron en Evolve 2016 y están disponibles como una vista previa para clientes probar y proporcionar comentarios.

Un tema se agrega a una aplicación de Xamarin.Forms mediante la inclusión de la **Xamarin.Forms.Theme.Base** de paquetes de Nuget, además de un paquete adicional que define un tema concreto (p ej. Xamarin.Forms.Theme.Light) o de lo contrario, se puede definir un tema local para la aplicación.

Hacer referencia a la [el tema claro](light.md) y [tema oscuro](dark.md) páginas para obtener instrucciones sobre cómo agregarlos a una aplicación, o visite el [tema personalizado de ejemplo](custom.md).

**Importante:** también debe seguir los pasos necesarios para [cargar ensamblados de tema (abajo)](#loadtheme) agregando código estereotipado a iOS `AppDelegate` y Android `MainActivity`. Se mejorará en versión preliminar futura.


## <a name="control-appearance"></a>Apariencia del control

El [luz](light.md) y [oscuro](dark.md) temas ambos definen una apariencia visual específica para los controles estándar. Una vez que agregue un tema para el diccionario de recursos de la aplicación, cambiará la apariencia de los controles estándar.

El marcado XAML siguiente muestra algunos controles comunes:

```xaml
<StackLayout Padding="40">
    <Label Text="Regular label" />
    <Entry Placeholder="type here" />
    <Button Text="OK" />
    <BoxView Color="Yellow" />
    <Switch />
</StackLayout>
```

Estas capturas de pantalla muestran estos controles con:

* Ningún tema aplicado
* Tema claro (solo diferencias sutiles a no tener tema)
* Tema oscuro

![](images/standard-none-sml.png "Controles sin los temas de") ![](images/standard-light-sml.png "controles con el tema claro") ![](images/standard-dark-sml.png "controles con el tema oscuro")

<a name="styleclass" />

## <a name="styleclass"></a>StyleClass

El `StyleClass` propiedad permite la apariencia de una vista que se puede cambiar según una definición de un tema.

El [luz](light.md) y [oscuro](dark.md) temas ambos definen tres diferentes aspectos de un `BoxView`: `HorizontalRule`, `Circle`, y `Rounded`. Este marcado muestra tres diferentes `BoxView`s con clases diferentes de estilo aplicado:

```xaml
<StackLayout Padding="40">
    <BoxView StyleClass="HorizontalRule" />
    <BoxView StyleClass="Circle" />
    <BoxView StyleClass="Rounded" />
</StackLayout>
```

Esto se representa con claro y oscuro como sigue:

![](images/boxview-light-sml.png "BoxView con un tema claro StyleClass") ![](images/boxview-dark-sml.png "BoxView con una StyleClass el tema oscuro")

<a name="builtin" />

## <a name="built-in-classes"></a>Clases integradas

Además de aplicar un estilo a automáticamente común controla la luz y los temas oscuros actualmente admiten las siguientes clases que se pueden aplicar mediante el establecimiento del `StyleClass` en estos controles:

**BoxView**

* HorizontalRule
* Círculo
* Redondeado

**Image**

* Círculo
* Redondeado
* Vista en miniatura

**Button**

* Default
* Principal
* Correcto
* Info
* Advertencia
* Peligro
* Vínculo
* Pequeño
* Grandes

**Label**

* Header
* Subencabezado
* Cuerpo
* Vínculo
* Inverso


## <a name="troubleshooting"></a>Solución de problemas

<a name="loadtheme" />

### <a name="could-not-load-file-or-assembly-xamarinformsthemelight-or-one-of-its-dependencies"></a>No se pudo cargar el archivo o ensamblado 'Xamarin.Forms.Theme.Light' o uno de sus dependencias

En la versión preliminar, los temas no pueda cargar en tiempo de ejecución. Agregue el código que se muestra a continuación, en los proyectos correspondientes para corregir este error.

**iOS**

En el **AppDelegate.cs** agregue las líneas siguientes después de `LoadApplication`

```csharp
var x = typeof(Xamarin.Forms.Themes.DarkThemeResources);
x = typeof(Xamarin.Forms.Themes.LightThemeResources);
x = typeof(Xamarin.Forms.Themes.iOS.UnderlineEffect);
```

**Android**

En el **MainActivity.cs** agregue las líneas siguientes después de `LoadApplication`

```csharp
var x = typeof(Xamarin.Forms.Themes.DarkThemeResources);
x = typeof(Xamarin.Forms.Themes.LightThemeResources);
x = typeof(Xamarin.Forms.Themes.Android.UnderlineEffect);
```


## <a name="related-links"></a>Vínculos relacionados

- [Ejemplo de ThemesDemo](https://github.com/xamarin/xamarin-forms-samples/tree/master/Themes/ThemesDemo)
