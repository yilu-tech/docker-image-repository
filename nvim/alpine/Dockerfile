FROM alpine:edge

ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8

RUN apk -U add perl git curl tzdata musl-locales nodejs npm the_silver_searcher neovim py3-pip python3 bash less openssh-client \
 && ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \ 

 && git clone git://github.com/ohmybash/oh-my-bash.git $HOME/.oh-my-bash --depth=1 \
 && cp $HOME/.oh-my-bash/templates/bashrc.osh-template $HOME/.bashrc \
 && sed -i 's|OSH_THEME="font"|OSH_THEME="minimal"|' $HOME/.bashrc \
 && sed -i 's/# DISABLE_AUTO_UPDATE/DISABLE_AUTO_UPDATE/g' $HOME/.bashrc \

 && apk add --virtual .build-deps gcc g++ python3-dev \
 && python3 -m pip install --user --upgrade pynvim \
 && apk del .build-deps \

 && sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim' \

 && mkdir -p $HOME/.config/nvim \
 && ln -sf /usr/bin/nvim /usr/bin/vi 

