FROM quay.io/keycloak/keycloak:20.0.3

ADD /theme/ /opt/keycloak/themes/ourTheme

RUN /opt/keycloak/bin/kc.sh build

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]