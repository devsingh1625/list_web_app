from flask import Flask, render_template, request, redirect, url_for
import os

app = Flask(__name__)

# Create a list to store our tasks with completion status
tasks = []


@app.route('/')
def home():
    return render_template('index.html', tasks=tasks)


@app.route('/add', methods=['POST'])
def add_task():
    task = request.form['task']
    tasks.append({'text': task, 'completed': False})
    return redirect(url_for('home'))


@app.route('/delete/<int:index>')
def delete_task(index):
    if 0 <= index < len(tasks):
        tasks.pop(index)
    return redirect(url_for('home'))


@app.route('/toggle/<int:index>')
def toggle_task(index):
    if 0 <= index < len(tasks):
        tasks[index]['completed'] = not tasks[index]['completed']
    return redirect(url_for('home'))


if __name__ == '__main__':
    port = int(os.environ.get('PORT', 5000))
    app.run(host='0.0.0.0', port=port, debug=False)
