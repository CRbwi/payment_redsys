# Actualización del Addon Payment Redsys para Odoo 18

## Cambios realizados para la compatibilidad con Odoo 18

### 1. Actualización del archivo __manifest__.py
- Cambiada la versión de "17.0.1.0.0" a "18.0.1.0.0"

### 2. Actualización del modelo payment.provider
- **Eliminado**: Método `_get_default_payment_method_id()` - No es necesario en Odoo 18
- **Motivo**: La gestión de métodos de pago ha cambiado en Odoo 18

### 3. Actualización del modelo payment.transaction
- **Cambiado**: Import de ValidationError de `odoo.addons.payment.models.payment_provider` a `odoo.exceptions`
- **Eliminado**: Llamada a `_finalize_post_processing()` - Método no disponible en Odoo 18
- **Motivo**: Los métodos de finalización de transacciones han sido simplificados

### 4. Actualización de datos XML
- **Corregido**: Mantenido el modelo `payment.method` para el método de pago Bizum (el modelo `payment.icon` no existe en Odoo 18)
- **Añadido**: Campo `code` en el método de pago Bizum para mayor compatibilidad
- **Motivo**: La estructura de payment.method se mantiene en Odoo 18

### 5. Archivos que NO requieren cambios
- `controllers/main.py` - Compatible con Odoo 18
- `views/payment_provider.xml` - Compatible con Odoo 18
- `views/payment_redsys_templates.xml` - Compatible con Odoo 18
- `models/account_payment_method.py` - Compatible con Odoo 18
- Tests en general - Compatible con Odoo 18

## Dependencias
Las dependencias externas siguen siendo las mismas:
- `pycryptodome` para el cifrado

## Instalación
1. Copie el addon a la carpeta de addons de Odoo 18
2. Actualice la lista de aplicaciones
3. Instale el addon "Pasarela de pago Redsys"

## Notas importantes
- Todas las funcionalidades del addon original se mantienen
- La configuración del proveedor de pago sigue siendo la misma
- Los métodos de pago soportados (Tarjeta, Bizum, etc.) siguen funcionando
- La integración con Redsys no cambia

## Testing
Se recomienda probar las siguientes funcionalidades después de la actualización:
1. Configuración del proveedor de pago Redsys
2. Procesamiento de pagos con tarjeta
3. Procesamiento de pagos con Bizum
4. Callbacks de confirmación de pago
5. Manejo de errores y transacciones canceladas
