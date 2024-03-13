from flask import Flask, render_template, request

app = Flask(__name__)

services = []


@app.route('/')
def index():
    return render_template('index.html', services=services)


@app.route('/post_service', methods=['POST'])
def post_service():
    title = request.form['title']
    description = request.form['description']
    price = request.form['price']
    services.append({'title': title, 'description': description, 'price': price})
    return render_template('D:\freelancemarketplace\index.html', services=services)


if __name__ == '__main__':
    app.run(debug=True)
