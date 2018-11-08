# Include cities and states

* Run on terminal
```
git clone https://github.com/oliveira-andre/includes_states_cities.git
```

* copy the file cities_includes.rb to /lib in your rails path and Run
```
rails runner lib/cities_includes.rb
```

* your state migration needs to looks like it
```
class CreateStates < ActiveRecord::Migration[5.2]
  def change
    create_table :states do |t|
      t.string :description

      t.timestamps
    end
  end
end

```



* your city migration needs to looks like it
```
class CreateCities < ActiveRecord::Migration[5.2]
  def change
    create_table :cities do |t|
      t.string :description
      t.references :state, foreign_key: true

      t.timestamps
    end
  end
end
```

* with this your schema will looks like it
```
create_table "cities", options: "ENGINE=InnoDB DEFAULT CHARSET=utf8", force: :cascade do |t|
    t.string "description"
    t.bigint "state_id"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
    t.index ["state_id"], name: "index_cities_on_state_id"
  end


create_table "states", options: "ENGINE=InnoDB DEFAULT CHARSET=utf8", force: :cascade do |t|
    t.string "description"
    t.datetime "created_at", null: false
    t.datetime "updated_at", null: false
  end

```
