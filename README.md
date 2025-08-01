<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# 🏢 Kodikas Laravel Multitenant Project

[![CI/CD Pipeline](https://github.com/KODIKAS-Software/laravel-multitenant-project/workflows/CI%2FCD%20Pipeline/badge.svg)](https://github.com/KODIKAS-Software/laravel-multitenant-project/actions)
[![Tests](https://github.com/KODIKAS-Software/laravel-multitenant-project/workflows/CI%2FCD%20Pipeline/badge.svg?event=push)](https://github.com/KODIKAS-Software/laravel-multitenant-project/actions)
[![Code Quality](https://github.com/KODIKAS-Software/laravel-multitenant-project/workflows/CI%2FCD%20Pipeline/badge.svg?job=code-quality)](https://github.com/KODIKAS-Software/laravel-multitenant-project/actions)
[![Auto Release](https://github.com/KODIKAS-Software/laravel-multitenant-project/workflows/CI%2FCD%20Pipeline/badge.svg?job=auto-release)](https://github.com/KODIKAS-Software/laravel-multitenant-project/actions)

Proyecto Laravel con paquete multitenant avanzado para SaaS empresarial. Diseñado exclusivamente para **Laravel 12.x** con enfoque latinoamericano/empresarial.

## ✨ Características Principales

- 🏢 **Paquete Multitenant Completo** - Sistema avanzado de multi-tenancy
- 🔐 **Control de Acceso Granular** - 8 tipos de usuario, 6 niveles de roles
- 🌐 **Middleware Empresarial** - 12+ tipos de parámetros de validación
- 🎯 **Detección Automática** - Tenants por subdomain, domain, path, header o session
- 🔒 **Restricciones Avanzadas** - IP, tiempo, suscripciones
- 🚀 **Laravel 12.x Ready** - Compatibilidad exclusiva con Laravel 12.x

## 📦 Estructura del Proyecto

```
kodikas-laravel-multitenant/
├── packages/kodikas/multitenant/     # Paquete principal multitenant
├── .github/workflows/               # CI/CD workflows
│   ├── code-quality.yml           # Validación de calidad de código
│   ├── security-scan.yml          # Escaneo de seguridad
│   ├── compatibility-tests.yml    # Tests de compatibilidad
│   └── performance-validation.yml # Validación de rendimiento
├── app/                           # Aplicación Laravel
├── tests/                         # Tests del proyecto
└── database/                      # Migraciones y seeders
```

## 🚀 Instalación Rápida

```bash
# Clonar el repositorio
git clone https://github.com/KODIKAS-Software/laravel-multitenant-project.git
cd laravel-multitenant-project

# Instalar dependencias
composer install

# Configurar entorno
cp .env.example .env
php artisan key:generate

# Ejecutar migraciones
php artisan migrate

# Publicar configuración del paquete multitenant
php artisan vendor:publish --provider="Kodikas\Multitenant\MultitenantServiceProvider"
```

## 📋 Requisitos del Sistema

- **PHP**: 8.2 o superior
- **Laravel**: 12.0 o superior (**EXCLUSIVAMENTE**)
- **Composer**: 2.0 o superior
- **Base de datos**: MySQL 8.0+, PostgreSQL 13+, SQLite 3.35+

## 🔧 Configuración del Paquete Multitenant

### 1. Configurar Middleware

En `bootstrap/app.php`:

```php
$app->withMiddleware(function (Middleware $middleware) {
    $middleware->alias([
        'tenant' => \Kodikas\Multitenant\Middleware\TenantMiddleware::class,
        'tenant.access' => \Kodikas\Multitenant\Middleware\TenantAccessMiddleware::class,
    ]);
});
```

### 2. Configurar Rutas

```php
Route::domain('{tenant}.example.com')->group(function () {
    Route::middleware(['tenant'])->group(function () {
        // Rutas específicas del tenant
    });
});
```

## 🧪 Testing

```bash
# Ejecutar tests del proyecto principal
vendor/bin/phpunit

# O usando artisan (Laravel)
php artisan test

# Ejecutar tests del paquete multitenant específicamente
cd packages/kodikas/multitenant
composer install
composer test

# Tests con cobertura de código
vendor/bin/phpunit --coverage-html coverage

# Tests de compatibilidad para Windows
test-compatibility.bat

# Tests de compatibilidad para Linux/Mac
./test-compatibility.sh

# Ejecutar tests específicos por categoría
vendor/bin/phpunit --testsuite=Feature
vendor/bin/phpunit --testsuite=Unit

# Tests con verbose output
vendor/bin/phpunit --verbose
```

## 🔒 Seguridad

- Escaneo automático de vulnerabilidades
- Validación de dependencias
- Análisis estático de código
- Verificación de credenciales hardcodeadas

## 📈 CI/CD Workflows

El proyecto incluye workflows automatizados para:

- **Code Quality**: Linting, style checking, static analysis
- **Security Scan**: Vulnerability scanning, dependency audit
- **Compatibility Tests**: Laravel 12.x + PHP 8.2/8.3 matrix
- **Performance Validation**: Load testing, coverage analysis

## 🤝 Contribuir

1. Fork el proyecto
2. Crear una rama feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit los cambios (`git commit -am 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Crear un Pull Request

Ver [CONTRIBUTING.md](CONTRIBUTING.md) para más detalles.

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver [LICENSE](LICENSE) para más detalles.

## 👥 Créditos

Desarrollado por **KODIKAS Software** - Miguel E Uicab Canabal

- 🌐 Website: [miguelmort.tech](https://miguelmort.tech)
- 📧 Email: miguel@kodikas.com
- 🐱 GitHub: [@MiguelMort09](https://github.com/MiguelMort09)

---

**¡Gracias por usar Kodikas Laravel Multitenant!** 🚀
