# Bagheera ElasticSearch #

Version: 0.6  

#### Adds support for ElasticSearch persistence to a bagheera server. ####

### Hazelcast ElasticSearchMapStore Configuration ###
If you want to configure a Hazelcast Map to persist data to ElasticSearch you can use the ElasticSearchMapStore. It will start a Node using the specified ElasticSearch config and index the data submitted to this map. This is probably of limited use if you're only using ElasticSearch as you could just use their interface directly.  Here's an example configuration:

	<map name="mymapname">
		<time-to-live-seconds>20</time-to-live-seconds>
		<backup-count>1</backup-count>
		<eviction-policy>NONE</eviction-policy>
		<max-size>0</max-size>
		<eviction-percentage>25</eviction-percentage>
		<merge-policy>hz.ADD_NEW_ENTRY</merge-policy>
		<!-- ElasticSearchMapStore -->
		<map-store enabled="true">
			<class-name>com.mozilla.bagheera.hazelcast.persistence.ElasticSearchMapStore</class-name>
			<write-delay-seconds>5</write-delay-seconds>
			<properties>
				<property name="hazelcast.elasticsearch.config.path">elasticsearch-socorro.yml</property>
				<property name="hazelcast.elasticsearch.index">socorro</property>
				<property name="hazelcast.elasticsearch.type.name">crash_reports</property>
			</properties>
		</map-store>
	</map>