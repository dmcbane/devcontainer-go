FROM qmcgaw/godevcontainer
RUN sed -i 's/#\(.*\/community\)/\1/' /etc/apk/repositories
RUN apk update && apk add --no-cache sudo shadow curl vim git

# ARG USERNAME=<<default username goes here>>
ARG USERNAME=gouser
ARG PASSWORD=developingwithgo
# ARG PASSWORD=<<default password goes here>>
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create the user
RUN addgroup -g $USER_GID $USERNAME
RUN adduser -s /bin/zsh -u $USER_UID -G $USERNAME -D $USERNAME
RUN echo "$USERNAME:$PASSWORD" | chpasswd
RUN echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME
RUN sudo chmod -R a+rw /go

# ********************************************************
# * Anything else you want to do like clean up goes here *
# ********************************************************

# [Optional] Set the default user. Omit if you want to keep the default as root.
USER $USERNAME

