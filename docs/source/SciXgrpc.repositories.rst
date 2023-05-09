.. SciXTemplatePipeline documentation master file, created by
   sphinx-quickstart on Tue May  2 15:24:55 2023.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

The gRPC Backend
====================================


.. image:: https://github.com/tjacovich/SciXTemplateRepository/actions/workflows/python_actions.yml/badge.svg
   :target: https://github.com/tjacovich/SciXTemplateRepository/actions/workflows/python_actions.yml
   :alt: Python CI actions

.. image:: https://coveralls.io/repos/github/tjacovich/SciXTemplateRepository/badge.svg?branch=main
   :target: https://coveralls.io/github/tjacovich/SciXTemplateRepository?branch=main
   :alt: Coverage Status



The Template gRPC API
---------------------------------

Because we are using ``AVRO`` instead of ``protobufs``, we cannot take advantage of the automatic API generation that ``gRPC`` offers. To help defray some of the cost of manually creating the API code, we have included some boilerplate code that initializes an ``INIT`` method, as well as a ``MONITOR`` method.

The API classes live in ``grpc_modules/template_grpc.py`` Each endpoint needs a ``Stub``, a ``Servicer``, a function that adds the endpoint to the ``gRPC`` server, as well as a main class that instantiates the grpc stream.
.. code-block:: python

   class TemplateInitStub(object):
      """The Stub for connecting to the Template init service."""

      def __init__(self, channel, avroserialhelper):
         """Constructor.
         Args:
         channel: A grpc.Channel.

         """

         self.initTemplate = channel.unary_stream(
               "/templateaapi.TemplateInit/initTemplate",
               request_serializer=avroserialhelper.avro_serializer,
               response_deserializer=avroserialhelper.avro_deserializer,
         )


   class TemplateInitServicer(object):
      """The servicer definition for initiating jobs with the Template pipeline."""

      def initTemplate(self, request, context):
         context.set_code(grpc.StatusCode.UNIMPLEMENTED)
         context.set_details("Method not implemented!")
         raise NotImplementedError("Method not implemented!")


   def add_TemplateInitServicer_to_server(servicer, server, avroserialhelper):
      """The actual methods for sending and receiving RPC calls."""

      rpc_method_handlers = {
         "initTemplate": grpc.unary_stream_rpc_method_handler(
               servicer.initTemplate,
               request_deserializer=avroserialhelper.avro_deserializer,
               response_serializer=avroserialhelper.avro_serializer,
         ),
      }
      generic_handler = grpc.method_handlers_generic_handler(
         "templateaapi.TemplateInit", rpc_method_handlers
      )
      server.add_generic_rpc_handlers((generic_handler,))


   class TemplateInit(object):
      """The definition of the Template gRPC API and stream connections."""

      @staticmethod
      def initTemplate(
         request,
         target,
         options=(),
         channel_credentials=None,
         call_credentials=None,
         insecure=False,
         compression=None,
         wait_for_ready=None,
         timeout=None,
         metadata=None,
      ):
         return grpc.experimental.unary_stream(
               request,
               target,
               "/templateaapi.TemplateInit/initTemplate",
               options,
               channel_credentials,
               insecure,
               call_credentials,
               compression,
               wait_for_ready,
               timeout,
               metadata,
         )
