# UUIDs no Laravel 12v

Laravel oferece suporte nativo para UUIDs (Universally Unique Identifiers) como chaves primárias em suas migrações e modelos Eloquent. Para usar UUIDs, você pode definir a coluna da chave primária como `uuid` em sua migração:

### Exemplo de migração:

```php
$table->uuid('id')->primary();
```

### Exemplo de modelo Eloquent:

Modelos Eloquent podem usar UUIDs como chaves primárias usando o trait `HasUuids`. Este trait é parte do Laravel e facilita a geração automática de UUIDs para os modelos.

```php
use Illuminate\Database\Eloquent\Concerns\HasUuids;

class User extends Model
{
    use HasUuids;

    public $incrementing = false;
    protected $keyType = 'string';
}
```

### Exemplo de modelo Eloquent: (Legado)
Se você preferir não usar o trait `HasUuids`, pode gerar UUIDs manualmente no método `booted` do modelo:

```php
use Illuminate\Database\Eloquent\Model;
use Illuminate\Support\Str;

class User extends Model
{
    public $incrementing = false;
    protected $keyType = 'string';

    protected static function booted()
    {
        static::creating(function ($model) {
            if (!$model->id) {
                $model->id = Str::uuid();
            }
        });
    }
}

```

### Usando UUIDs para chaves estrangeiras

Além disso, você pode usar UUIDs para chaves estrangeiras em suas migrações:

```php
$table->foreignUuid('user_id')->constrained();
```

### Configuração adicional

Após fazer essas alterações, certifique-se de limpar o cache de configuração para que as mudanças sejam aplicadas:


```bash
php artisan config:clear
```