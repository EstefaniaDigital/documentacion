---
sidebar_position: 2
---

# Modelos 

Este componente se encarga de manipular, gestionar y actualizar los datos de una base de datos. No contiene ninguna lógica que describa como presentar los datos a un usuario.

como los modelos son basicamente lo mismo que las migraciones, este documento limita solo las funciones de los modelos y sus relaciones

## Estado 

la particularidad de esta tabla es que esta en un termino singular, por defecto laravel asume que todas las tablas estan en plural por lo que es necesario cambiarlo asi:

```php
    protected $table = 'estado';
```
y las tablas con las que tiene relacion son de tipo **hasOne** 1:1.

```php
    
    public function user(){
        return $this->hasOne(User::class);
    }

    public function mision(){
        return $this->hasOne(Mision::class);
    }

    public function logica(){
        return $this->hasOne(Logica::class);
    }

    public function image(){
        return $this->hasOne(Image::class);
    }
```

## Empresa 

Al igual que estado esta tabla esta en singular por lo que es necesario cambiarlo asi:

```php
    protected $table = 'empresa';
```
y las tablas con las que tiene relacion son de tipo **belongsTo** 1:1.

```php
    public function estado(){
        return $this->belongsTo(Estado::class,'estadoId');
    }
```

## Producto

las tablas con las que tiene relacion son de tipo **hasOne** 1:1.

```php
    public function etiqueta(){
        return $this->hasOne(Etiqueta::class);
    }
```

## Users

las tablas con las que tiene relacion son de tipo **belongsTo** 1:1.

```php
    
    public function empresa(){
        return $this->belongsTo(Empresa::class, 'empresaId');
    }
    
    public function estado(){
        return $this->belongsTo(Estado::class, 'estado');
    }
```

## Modelo

las tablas con las que tiene relacion son de tipo **belongsTo** y **hasMany** 

```php

    public function empresa(){
        return $this->belongsTo(Empresa::class, 'empresaId');
    }
    public function estado(){
        return $this->belongsTo(Estado::class, 'estado');
    }
        public function image(){
        return $this->hasMany(Image::class);
    }
    public function favorite(){
        return $this->hasMany(Favorite::class);
    }
```



## Mision

Al igual que estado esta tabla esta en singular por lo que es necesario cambiarlo asi:

```php
    protected $table = 'mision';
```
y las tablas con las que tiene relacion son de tipo **belongsTo** 1:1.

```php
    public function estado(){
        return $this->belongsTo(Estado::class, 'estado');
    }
    public function user(){
        return $this->belongsTo(User::class, 'userId');
    }
    public function modelo(){
        return $this->belongsTo(Modelo::class, 'modeloId');
    }
```

## Logica

Al igual que estado esta tabla esta en singular por lo que es necesario cambiarlo asi:

```php
    protected $table = 'logica';
```
y las tablas con las que tiene relacion son de tipo **belongsTo** 1:1.

```php
    public function estado(){
        return $this->belongsTo(Estado::class,'estadoId');
    }
```

## Imagen

Al igual que estado esta tabla esta en singular por lo que es necesario cambiarlo asi:

```php
    protected $table = 'image';
```
y las tablas con las que tiene relacion son de tipo **belongsTo**, **hanOne** y **hasMany** 

```php
    public function users(){
        return $this->belongsTo('users');
    }
    public function mision(){
        return $this->belongsTo('mision');
    }
    public function estado(){
        return $this->hasOne('estado');
    }
    public function favorite(){
        return $this->hasMany(Favorite::class);
    }
    public function checkFav(User $user){
        return $this->favorite('userId', $user->id);
    }
    public function veredicto(){
        return $this->hasOne(Veredicto::class);
    }

```

## Veredicto 

y las tablas con las que tiene relacion son de tipo **hasMany** 

```php
      public function image(){
        return $this->hasMany(Image::class);
    }

```

## detalles de misiones en adelante estan pendientes por que todavia no se han definido
<!-- 
## Detalles Misiones

Al igual que estado esta tabla esta en singular por lo que es necesario cambiarlo asi:

```php
    protected $table = 'empresa';
```
y las tablas con las que tiene relacion son de tipo **belongsTo** 1:1.

```php
    public function estado(){
        return $this->belongsTo(Estado::class,'estadoId');
    }
```

## Empresa 

Al igual que estado esta tabla esta en singular por lo que es necesario cambiarlo asi:

```php
    protected $table = 'empresa';
```
y las tablas con las que tiene relacion son de tipo **belongsTo** 1:1.

```php
    public function estado(){
        return $this->belongsTo(Estado::class,'estadoId');
    }
``` --> -->