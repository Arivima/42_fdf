NAME				= fdf

LIB_DIR				= ./lib

LIBFT_DIR			= $(LIB_DIR)/libft
LIBFT_A				= $(LIBFT_DIR)/libft.a

MLX_DIR				= $(LIB_DIR)/mlx_linux
MLX_A				= $(MLX_DIR)/libmlx_Linux.a

PRINTF_DIR			= $(LIB_DIR)/ft_printf
PRINTF_A			= $(PRINTF_DIR)/libftprintf.a

LIB_A				= $(LIBFT_A) $(PRINTF_A) $(MLX_A)

HEAD_DIR			= ./include

FILES				= \
						main.c\
						1_init.c\
						2_parsing_1.c\
						2_parsing_2.c\
						3_pixel_manipulation_1.c\
						3_pixel_manipulation_2_bonus.c\
						3_pixel_manipulation_3_bonus.c\
						4_draw_1.c\
						4_draw_2.c\
						5_draw_utils.c\
						5_draw_utils_colors_1.c\
						5_draw_utils_colors_2.c\
						6_events.c\
						7_utils_1.c\
						7_utils_2.c\
						8_exit.c\
						# _delete.c\
						# _testing.c\

SRCS_DIR			=	./srcs
SRCS				= $(addprefix $(SRCS_DIR)/,$(FILES))

OBJS_DIR			=	./objs
OBJS				= $(patsubst $(SRCS_DIR)%,$(OBJS_DIR)%,$(SRCS:.c=.o))

INCLUDES			= -I $(LIBFT_DIR) -I $(MLX_DIR) -I $(PRINTF_DIR) -I $(HEAD_DIR)
CFLAGS 				= -Wall -Wextra -Werror $(INCLUDES) 
MLX_FLAGS			= $(MLX_A) -L $(MLX_DIR) -I $(MLX_DIR) -lXext -lX11 -lm -lz

GREEN 				= "\033[01;32m"
RESET 				= "\033[00m"

all:				$(NAME)

$(NAME):			$(LIB_A) $(OBJS)
					@gcc $(CFLAGS)  $(OBJS) $(MLX_FLAGS) $(LIB_A) -o $(NAME)
					@echo "FDF successfully compiled"

$(OBJS_DIR)/%.o: $(SRCS_DIR)/%.c
					@mkdir -p $(@D)
					@gcc -c $(CFLAGS) $< -o $@

$(OBJS):			| $(OBJS_DIR)

$(OBJS_DIR):
					@mkdir $(OBJS_DIR)

$(LIB_A) :			
					@printf "Making libft..." && make -C $(LIBFT_DIR) && echo "Libft successfully compiled"
					@printf "Making printf..." && make -C $(PRINTF_DIR) && echo "Printf successfully compiled"
					@printf "Making mlx..." && make -C $(MLX_DIR) && echo "Mlx successfully compiled"

clean:				
					make clean -C $(LIBFT_DIR)
					make clean -C $(PRINTF_DIR)
					make clean -C $(MLX_DIR)
					rm -f $(OBJS)
					echo "Successfully cleaned"

fclean: 			clean
					@make fclean -C $(LIBFT_DIR)
					@make fclean -C $(PRINTF_DIR)
					@make clean -C $(MLX_DIR)
					@rm -f $(NAME)
					@rm -rf $(OBJS_DIR)
					@echo "Successfully f-cleaned"

bis:				
					@rm -f $(OBJS)
					@echo "Successfully cleaned objects"
					make

re: 				fclean all
.PHONY: 			all clean fclean re bis