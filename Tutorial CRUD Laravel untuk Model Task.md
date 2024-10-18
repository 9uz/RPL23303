# Tutorial CRUD Laravel untuk Model Task

## 1. Model
Pertama, buat model Task dengan menggunakan perintah Artisan:

```bash
php artisan make:model Task
```

Buka file app/Models/Task.php dan tambahkan kode berikut:

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Task extends Model
{
    use HasFactory;

    protected $fillable = ['title', 'description', 'status', 'due_date', 'user_id'];

    public function user()
    {
        return $this->belongsTo(User::class);
    }
    ......................
    .....................
}
```

## 2. Controller

Buat TaskController dengan perintah Artisan:

```bash
php artisan make:controller TaskController --resource
```

Buka file app/Http/Controllers/TaskController.php dan implementasikan metode CRUD dan 
Tambahkan Fungsi berikut
```php

    public function create()
    {
        return view('tasks.create');
    }

    public function store(Request $request)
    {
        $request->validate([
            'title' => 'required',
            'description' => 'nullable',
            'status' => 'required|in:pending,in_progress,completed',
            'due_date' => 'required|date',
        ]);
        
        $request->request->add(['user_id' => 1]);
        $task = Task::create($request->all());
        return redirect()->route('tasks.index')->with('success', 'Task created successfully.');
    }

    public function show(string $id)
    {
        $task=Task::find($id);
        return view('tasks.show', ['task'=>$data]);
    }

    public function edit(Task $task)
    {
        return view('tasks.edit', compact('task'));
    }

    public function update(Request $request, Task $task)
    {
        $request->validate([
            'title' => 'required',
            'description' => 'nullable',
            'status' => 'required|in:pending,in_progress,completed',
            'due_date' => 'required|date',
        ]);

        $task->update($request->all());
        return redirect()->route('tasks.index')->with('success', 'Task updated successfully.');
    }

    public function destroy(Task $task)
    {
        $task->delete();
        return redirect()->route('tasks.index')->with('success', 'Task deleted successfully.');
    }

```

## 3. Routes

Tambahkan routes berikut di file routes/web.php:
```php
use App\Http\Controllers\TaskController;

Route::resource('tasks', TaskController::class);
```

## 4. Views

Buat folder resources/views/tasks dan buat file-file berikut:

### 4.1 index.blade.php

```html
@extends('layouts.app')

@section('title', 'Task manager')

@section('content')
    <h1>Tasks</h1>
    <a href="{{ route('tasks.create') }}" class="btn btn-primary">Create New Task</a>
    
    <table class="table mt-3">
        <thead>
            <tr>
                <th>Title</th>
                <th>Status</th>
                <th>Due Date</th>
                <th>Actions</th>
            </tr>
        </thead>
        <tbody>
            @foreach($tasks as $task)
                <tr>
                    <td>{{ $task->title }}</td>
                    <td>{{ $task->status }}</td>
                    <td>{{ $task->due_date }}</td>
                    <td>
                        <a href="{{ route('tasks.show', $task) }}" class="btn btn-sm btn-info">View</a>
                        <a href="{{ route('tasks.edit', $task) }}" class="btn btn-sm btn-warning">Edit</a>
                        <form action="{{ route('tasks.destroy', $task) }}" method="POST" style="display: inline-block;">
                            @csrf
                            @method('DELETE')
                            <button type="submit" class="btn btn-sm btn-danger" onclick="return confirm('Are you sure?')">Delete</button>
                        </form>
                    </td>
                </tr>
            @endforeach
        </tbody>
    </table>
@endsection
```

### 4.2 create.blade.php

```html
@extends('layouts.app')

@section('content')
    <h1>Create New Task</h1>
    
    <form action="{{ route('tasks.store') }}" method="POST">
        @csrf
        <div class="form-group">
            <label for="title">Title</label>
            <input type="text" name="title" id="title" class="form-control" required>
        </div>
        <div class="form-group">
            <label for="description">Description</label>
            <textarea name="description" id="description" class="form-control"></textarea>
        </div>
        <div class="form-group">
            <label for="status">Status</label>
            <select name="status" id="status" class="form-control" required>
                <option value="pending">Pending</option>
                <option value="in_progress">In Progress</option>
                <option value="completed">Completed</option>
            </select>
        </div>
        <div class="form-group">
            <label for="due_date">Due Date</label>
            <input type="date" name="due_date" id="due_date" class="form-control" required>
        </div>
        <button type="submit" class="btn btn-primary">Create Task</button>
    </form>
@endsection
```

### 4.3 show.blade.php

```html
@extends('layouts.app')

@section('content')
    <h1>Task Details</h1>
    
    <div>
        <strong>Title:</strong> {{ $task->title }}
    </div>
    <div>
        <strong>Description:</strong> {{ $task->description }}
    </div>
    <div>
        <strong>Status:</strong> {{ $task->status }}
    </div>
    <div>
        <strong>Due Date:</strong> {{ $task->due_date }}
    </div>
    
    <a href="{{ route('tasks.edit', $task) }}" class="btn btn-warning">Edit</a>
    <form action="{{ route('tasks.destroy', $task) }}" method="POST" style="display: inline-block;">
        @csrf
        @method('DELETE')
        <button type="submit" class="btn btn-danger" onclick="return confirm('Are you sure?')">Delete</button>
    </form>
@endsection
```

### 4.4 edit.blade.php

```html
@extends('layouts.app')

@section('content')
    <h1>Edit Task</h1>
    
    <form action="{{ route('tasks.update', $task) }}" method="POST">
        @csrf
        @method('PUT')
        <div class="form-group">
            <label for="title">Title</label>
            <input type="text" name="title" id="title" class="form-control" value="{{ $task->title }}" required>
        </div>
        <div class="form-group">
            <label for="description">Description</label>
            <textarea name="description" id="description" class="form-control">{{ $task->description }}</textarea>
        </div>
        <div class="form-group">
            <label for="status">Status</label>
            <select name="status" id="status" class="form-control" required>
                <option value="pending" {{ $task->status == 'pending' ? 'selected' : '' }}>Pending</option>
                <option value="in_progress" {{ $task->status == 'in_progress' ? 'selected' : '' }}>In Progress</option>
                <option value="completed" {{ $task->status == 'completed' ? 'selected' : '' }}>Completed</option>
            </select>
        </div>
        <div class="form-group">
            <label for="due_date">Due Date</label>
            <input type="date" name="due_date" id="due_date" class="form-control" value="{{ $task->due_date }}" required>
        </div>
        <button type="submit" class="btn btn-primary">Update Task</button>
    </form>
@endsection
```

## 5. Middleware (Optional)

Jika Anda ingin menambahkan autentikasi ke CRUD Task, Anda bisa menambahkan middleware 'auth' ke TaskController. Tambahkan kode berikut di konstruktor TaskController:

```php
public function __construct()
{
    $this->middleware('auth');
}
```
