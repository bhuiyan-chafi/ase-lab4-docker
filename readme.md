# Firing up the app in docker

    - add the .dockerignore file first so that you can avoid adding the venv folder
    - add the Dockerfile
    - docker build -t lab3 .
    # in mac you cannot use 5000 port because its being used by the airplay
    - docker run -p 5005:5000 --name lab3 lab3-app
    - change app.run(debug=True) to app.run(host="0.0.0.0", port=5000, debug=True) otherwise flask will not allow external connections. This means the server is running locally for all connections.
    - rebuild your image: docker build -t lab3-app .
    - start a new container

# create a volume and attach it to the container

    - docker volume create lab3
    - docker run -p 5005:5000 --name lab3 --mount source=lab3,target=/app lab3-app

# The Dockerfile_exception

I don't know what was wrong first time! Even chatgpt said some bullshit but the solution works keeping app.run(debug=True). You can see the Dockerfile_exception for the changes. The debugger might not work becuse I haven't added any volumes but I think if I do so it will work. But its sure that the debug=True inside app.run() doesn't work. You have to mention the --debug inside the dockerfile.
