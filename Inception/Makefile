all: 
	mkdir -p /home/itchinda/data/mariadb
	mkdir -p /home/itchinda/data/wordpress
	docker compose -f ./srcs/docker-compose.yml build
	docker compose -f ./srcs/docker-compose.yml up -d

stop:
	docker container stop nginx mariadb wordpress

up:
	docker compose -f ./srcs/docker-compose.yml up -d

ls:
	docker ps
	docker volume ls
	docker network ls


logs:
	docker logs wordpress
	docker logs mariadb
	docker logs nginx

mariadb:
	docker exec -it mariadb bash

clean:
	docker container stop nginx mariadb wordpress
	docker network rm inception

fclean: clean
	@sudo rm -rf /home/itchinda/data/mariadb/*
	@sudo rm -rf /home/itchinda/data/wordpress/*
	@docker system prune -af

re: fclean all

.Phony: all logs clean fclean