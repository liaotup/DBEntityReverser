# 实体类结构
* 文件
    * 类名声明
        * Tables Comment
        * 类注解
             * 必要注解 
                * 数据库表名mapping信息
                    * table_name                    
                    * ...                
            * Annotation Extend (业务逻辑等)
    * 类属性声明
        * Propertie Comment
        * 类属性注解
            * 必要注解 
                * 数据库字段mapping信息
                    * id
                    * key_gen_type
                    * col_name
                    * col_size
                    * col_type
                    * nullable
                    * ...
                * 关联注解(ManyToOne、OneToMany)
            * Annotation Extend (业务逻辑等)
    * 属性 Getter (gen by property List)
    * 属性 Setter (gen by property List)
    * Hash Method  (gen by property List)
    * Equal Method (default)

    ```JSON
[
    {
        'imports': [
            'import com.module.dao.entity.City'
        ],
        'className': 'UserInfo',
        'description': '用户表',
        'annotations': {
            '@Entity(name = "user_info")'
        },
        'properties': {
            'id': {
                'type': 'Integer',
                'description': '用户ID',
                'annotations': {
                    '@Id',
                    '@GeneratedValue',
                    '@Column(name = "id", unique = true, nullable = false)'
                }
            },
            'ServiceCity'{
                'type': 'CityInfo',
                'description': '用户ID',
                'annotations': {
                    '@Column(name = "service_city", nullable = false)',
                    '@ManyToOne',
                    '@JoinColumn(name = "city_info", nullable = false)'
                }

            }
        }
    },
    {
        'imports': [],
        'className': 'CityInfo',
        'description': '城市信息',
        'annotations': {
            '@Entity(name = "city_info")'
        },
        'properties': {
            'id': {
                'type': 'Integer',
                'description': '城市ID',
                'annotations': {
                    '@Id',
                    '@GeneratedValue',
                    '@Column(name = "id", unique = true, nullable = false)'
                }
            },
            'cityName'{
                'type': 'String',
                'description': '城市名称',
                'annotations': {
                    '@Column(name = "city_name", nullable = false)'
                }

            }
        }
    },
    ...
]
    ```
