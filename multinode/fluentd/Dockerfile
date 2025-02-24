FROM fluentd:v1.18-debian-1
USER root

ENV BUNDLE_SILENCE_ROOT_WARNING=1
COPY Gemfile Gemfile
RUN bundle install

USER fluent