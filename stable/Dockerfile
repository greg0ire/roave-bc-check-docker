FROM nyholm/roave-bc-check:base
MAINTAINER Tobias Nyholm <tobias.nyholm@gmail.com>

ENV BC_CHECK_VERSION stable

RUN composer global config minimum-stability dev \
    && composer global config prefer-stable true

RUN composer global require roave/backward-compatibility-check \
    && composer global show | grep backward-compatibility-check
