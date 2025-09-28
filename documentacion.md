# Como documentar código en diferentes lenguajes de programación

---

## Phyton

* En **Phyton** se documenta en la primera declaración de un módulo, función, clase o método.
* Se suele usar **comillas triples** (""" o ''').
* **Ejemplo:**
  def calcular_area_circulo(radio):
     """Calcula el área de un círculo dado su radio.

    Args:
        radio (float): El radio del círculo. Debe ser un número positivo.

    Returns:
        float: El área calculada del círculo.
               Retorna -1 si el radio es negativo.
    """
    if radio < 0:
        return -1
    pi = 3.14159
    return pi * (radio ** 2)

---
## JavaScript

* Los comentarios de **JS** comienzan con **/\*\*** y terminan con **\*/**. Utiliza etiquetas **(tags)** como @param, @returns y @description para describir elementos específicos.
* **Ejemplo:**
**/\*\***
 \* Calcula el área de un círculo a partir de su radio.
 \*
 \* @param {number} radio El radio del círculo. Debe ser un número positivo.
 \* @returns {number} El área calculada del círculo. Devuelve -1 si el radio es negativo.
 **\*/**
function calcularAreaCirculo(radio) {
  if (radio < 0) {
    return -1;
  }
  return Math.PI * (radio ** 2);
}

---

## PHP

* En **PHP** funcionan igual que en JavaScript
* **Ejemplo:**
  \<?php

**/\*\***
 \* Calcula el área de un círculo a partir de su radio.
 \*
 \* @param float  El radio del círculo. Debe ser un número positivo.
 \* @return float El área calculada del círculo. Devuelve -1 si el radio es negativo.
 **\*/**
function calcularAreaCirculo(float \$radio): float
{
    if ($radio < 0) {
        return -1.0;
    }
    return pi() * ($radio ** 2);
}

?>